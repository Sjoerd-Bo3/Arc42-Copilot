# 5. Building Block View

## 5.1 Level 1 — White-box Overall System

```plantuml
@startuml
skinparam shadowing false
skinparam componentStyle rectangle

rectangle "Planning Service(s)" as Planning
rectangle "Notification Service\n(optional)" as Notify
rectangle "Parts Status Source\n(optional)" as Parts

package "Pitstop (overall system)" #OrangeRed {
  rectangle "Admin Overview UI" as AdminUI
  rectangle "Workshop View UI\n(degraded mode capable)" as WorkshopUI
  rectangle "Pitstop Backend" as Backend
  rectangle "Sync & Integration Layer" as Sync
  rectangle "Audit/Event Log" as Audit
  database "Pitstop DB" as DB
}

Planning --> Sync : appointments\n(+changes)
Sync --> Planning : status updates\n(reschedule proposals)

AdminUI --> Backend : HTTPS/JSON\nwork orders, planning views
WorkshopUI --> Backend : WebSocket/JSON\nlive board + updates

Backend --> DB : read/write
Backend --> Audit : append events
Sync --> Backend : mapped changes\n(commands/events)
Backend --> Sync : integration events

Backend --> Parts : query parts status\n(reference only)
Backend --> Notify : send updates\n(optional)
Notify --> AdminUI : delivery status\n(optional)
@enduml
```

### Black-boxes (Level 1)

| Block | Responsibility | Key Interfaces |
|-------|---------------|----------------|
| Admin Overview UI | Dashboard, coordination, customer comms support | HTTPS/JSON to Backend |
| Workshop View UI | Bay/task board, fast updates, degraded mode | WebSocket/JSON to Backend |
| Backend | Core domain + APIs + orchestration | HTTPS/JSON + WS + internal module interfaces |
| Sync & Integration | Mapping + sync strategy per planning vendor | REST/JSON, webhooks, retry |
| Audit/Event Log | Immutable history for accountability + analytics | Append/read APIs |
| DB | Operational persistence | SQL (implementation-specific) |

## 5.2 Level 2 — Pitstop Backend

```plantuml
@startuml
skinparam shadowing false
skinparam componentStyle rectangle

package "Pitstop Backend (white-box)" {
  rectangle "API Layer\n(REST + WS)" as Api
  rectangle "AuthN/AuthZ\n(RBAC)" as Auth

  package "Modules (black-boxes)" {
    rectangle "Work Order Module" as WorkOrders
    rectangle "Workshop Module" as Workshop
    rectangle "Admin Module" as Admin
    rectangle "Customer/Vehicle Module" as Customer
    rectangle "Reporting Read Models" as Reporting
  }

  package "Integration Ports" {
    rectangle "Planning Port" as PlanningPort
    rectangle "Notification Port" as NotifyPort
    rectangle "Parts Status Port" as PartsPort
  }

  rectangle "Audit Writer" as AuditWriter
  database "Pitstop DB" as DB
}

Api --> Auth
Api --> WorkOrders
Api --> Workshop
Api --> Admin
Api --> Customer
Api --> Reporting

WorkOrders --> AuditWriter
Workshop --> AuditWriter
Admin --> AuditWriter
AuditWriter --> DB

WorkOrders --> PlanningPort
Workshop --> PlanningPort
Admin --> NotifyPort
WorkOrders --> PartsPort
@enduml
```

### Building blocks (Level 2)

| Element | Responsibility | Depends on |
|---------|---------------|------------|
| Work Order Module | Core logic for orders | Customer, Audit |
| Workshop Module | Mechanic task management | WorkOrders, Audit |
| Admin Module | Configuration and overrides | Audit |
| Customer/Vehicle Module | Shared entity data | Audit |
| Reporting | Read-optimized views | Domain Events |
| Planning Port | Adapter for Planning Service | External |
| Notification Port | Adapter for Notification Service | External |
| Parts Status Port | Adapter for parts/inventory query | External |
| Audit Writer | Centralized compliance logging | DB |
| API Layer | Protocol handling (HTTP/WS) | Auth, Modules |

**Notes:**

- Modules contain domain rules; ports isolate vendor protocols/mapping.
- Reporting read models can be optimized independently (avoid OLTP pain).
