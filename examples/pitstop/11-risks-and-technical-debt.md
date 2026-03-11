# 11. Risks and Technical Debt

## Risks

| Risk | Why it matters | Mitigation |
|------|---------------|------------|
| Integration ambiguity per Planning Vendor | Different semantics (cancellations, reschedules, no-shows) cause inconsistent work orders | Vendor mapping spec + contract tests; vendor-specific logic in adapters |
| Offline sync conflicts | Concurrent edits in degraded mode create conflict resolution complexity | Simple rules (append notes; validate status transitions); "needs foreman review" path |
| Backlog growth in sync queue | Vendor outage delays updates, delaying customer comms | Monitor `sync_queue_depth`; circuit breaker; dead-letter queue + ops playbook |
| WebSocket instability | Real-time UX degrades unpredictably in harsh garage networks | Configurable fallback to polling; reconnect UX; track disconnect rates |
| Audit log volume | Auditability creates data bloat; dashboards can overload OLTP queries | Read models; partition audit table; retention policies; optional replica |

## Known Technical Debt (intentional for v1)

| Debt item | Rationale | Revisit when |
|-----------|-----------|-------------|
| Single backend instance per garage (no HA) | Acceptable for v1; small garages don't need HA | Chain deployments or when uptime SLA increases |
| Minimal conflict resolution UI | Acceptable initially | Prioritize based on observed conflict frequency |
