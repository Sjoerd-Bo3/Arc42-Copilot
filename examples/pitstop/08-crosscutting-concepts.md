# 8. Crosscutting Concepts

## 8.1 Identity and Access (RBAC)

**Implementation:** JWT bearer tokens with policy-based authorization.

**Claims:**

- `role`: `Mechanic`, `Foreman`, `ServiceAdvisor`
- `garageId`: used for tenant/site scoping
- `permissions`: optional fine-grained list for exceptions

**Policy mapping:**

| Role | Permissions |
|------|------------|
| Mechanic | Update status for assigned work orders |
| Foreman | Override conflicts + reprioritize bays |
| Service Advisor | Customer communication, priority changes |

**Enforcement:** API endpoints require policies (`WorkOrders.Read`, `WorkOrders.UpdateStatus`, `Planning.Sync.Write`). Workshop actions use server-side authorization (don't trust the UI).

## 8.2 Real-time Updates

- Workshop UI uses **WebSocket** (or SignalR-like hub semantics).
- Admin UI uses HTTPS + incremental refresh.
- Both consume the same "work order changed" message format.

**Config-driven:** Controlled by `Pitstop:Realtime:Transport` and `FallbackToPollingSeconds`.

**Payload example:**

```json
{
  "type": "WorkOrderChanged",
  "workOrderId": "WO-7781",
  "version": 42,
  "changedFields": ["status", "notePreview", "updatedAt"],
  "status": "WaitingForParts",
  "updatedAt": "2026-01-12T10:41:00+01:00"
}
```

## 8.3 Degraded-mode Operation

Workshop UI stores updates in a **local outbox queue** (IndexedDB / local storage). Each item includes an **idempotency key**.

**Queue item example:**

```json
{
  "idempotencyKey": "WO-7781:42:mechanic-17:10:41:12",
  "workOrderId": "WO-7781",
  "command": "ChangeStatus",
  "payload": { "status": "WaitingForParts", "note": "Brake pads not in stock" },
  "queuedAt": "2026-01-12T10:41:00+01:00"
}
```

**Replay rules:**

- On reconnect: replay in order, stop on hard conflicts, show resolution UI.
- Notes are append-only (safe merge).
- Status changes validated by state machine (reject invalid transitions).

**Config:** If `ConnectivityMode = OfflineFirst`, UI always queues first and sends async. If `OnlineFirst`, UI sends immediately and only queues on failure.

## 8.4 Auditability

Every significant change writes an **audit event** (append-only table or event store).

**Audit event schema:**

```json
{
  "eventId": "evt-9b1c",
  "aggregateType": "WorkOrder",
  "aggregateId": "WO-7781",
  "eventType": "StatusChanged",
  "occurredAt": "2026-01-12T10:41:00+01:00",
  "actor": { "userId": "mechanic-17", "role": "Mechanic" },
  "reason": "WaitingForParts",
  "data": {
    "from": "InProgress",
    "to": "WaitingForParts",
    "note": "Brake pads not in stock"
  },
  "correlationId": "corr-2f8d"
}
```

## 8.5 Integrations

Sync adapter uses:

- Retry with exponential backoff (`MaxRetries`)
- Circuit breaker when vendor returns repeated 5xx/timeout
- Dead-letter queue after retry budget exhausted

**Config:**

```json
{
  "Pitstop": {
    "Sync": {
      "MaxRetries": 10,
      "InitialBackoffSeconds": 2,
      "CircuitBreaker": { "FailureThreshold": 5, "OpenSeconds": 30 }
    }
  }
}
```

**User-facing behavior:** Admin UI shows "Planning sync delayed (vendor outage). Updates queued."

## 8.6 Observability

**Structured logs** with `correlationId`, `workOrderId`, `garageId`.

**Key metrics:**

| Metric | Purpose |
|--------|---------|
| `sync_queue_depth` | Sync backlog health |
| `ws_connected_clients` | Real-time coverage |
| `status_update_latency_ms` (p95) | Consistency target |
| `integration_failures_total` | Vendor health |

**Alert example:** `sync_queue_depth > 100 for 10 minutes` indicates vendor down or credentials broken.
