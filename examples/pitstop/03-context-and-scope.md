# 3. Context and Scope

Pitstop sits between:

- **Planning** (appointments and promises),
- **Admin** (coordination and customer communication),
- **Workshop execution** (reality: progress, delays, extra work),

and keeps them synchronized.

## 3.1 Business Context

```plantuml
@startuml
skinparam shadowing false
skinparam componentStyle rectangle

actor "Service Advisor" as Advisor
actor "Workshop Foreman" as Foreman
actor Mechanic
actor Customer

rectangle "Planning Service" as Planning
rectangle Pitstop as "Pitstop" #OrangeRed
rectangle "Admin Overview" as AdminUI
rectangle "Workshop View" as WorkshopUI
rectangle "Notification Service\n(optional)" as Notify

Customer -> Advisor : appointment\nquestions/updates
Advisor --> Planning : create/adjust\nappointment
Planning --> Pitstop : appointments\n(+changes)
Pitstop --> Planning : status updates\n(reschedule proposals)

Advisor --> AdminUI : coordinate\ncommunicate
Foreman --> AdminUI : priorities\nbay allocation
Mechanic --> WorkshopUI : progress\nnotes

AdminUI --> Pitstop : assign/prioritize\nwork orders
WorkshopUI --> Pitstop : status updates\n(findings, parts)
Pitstop --> Notify : send customer\nnotifications
Notify -> Customer : SMS/email
@enduml
```

| Actor / System | Responsibility | Exchanges with Pitstop |
|----------------|---------------|------------------------|
| Customer | Brings car, receives updates | ETA updates (via advisor/portal) |
| Service Advisor | Manages appointment and expectations | Priority changes, notes, customer communication |
| Workshop Foreman | Orchestrates execution | Assignments, reprioritization |
| Mechanic | Performs work | Status updates, findings, time spent |
| Planning Service | Owns schedule/time slots | Appointment import, reschedule suggestions |
| Notifications (optional) | Contact customers | SMS/email updates |

## 3.2 Technical Context

```plantuml
@startuml
skinparam shadowing false
skinparam componentStyle rectangle

rectangle "Planning Service" as Planning
rectangle "Pitstop Backend" as Backend #OrangeRed
rectangle "Admin Overview UI" as AdminUI
rectangle "Workshop View UI" as WorkshopUI
rectangle "Notification Service\n(optional)" as Notify

Planning --> Backend : REST: Appointments\n(+ optional Webhooks)
Backend --> Planning : REST: Status Updates\n(Delay, Ready, Reschedule)

AdminUI --> Backend : HTTPS: Work Orders,\nAssignments, Priorities
Backend --> AdminUI : HTTPS: Dashboard Data

WorkshopUI <--> Backend : WebSocket: Live board\nStatus + Notes

Backend --> Notify : REST: Send SMS/email
@enduml
```

### Interfaces

| Peer | Interface | Direction | Protocol/Format | Notes |
|------|-----------|-----------|-----------------|-------|
| Planning Service | Appointments API | Inbound | REST/JSON | Full import + incremental sync |
| Planning Service (optional) | Webhooks | Inbound | HTTP/JSON | Push appointment changes |
| Pitstop to Planning | Status updates | Outbound | REST/JSON | Delay, ready, reschedule proposal |
| Admin Overview UI | Work Orders API | Bidirectional | HTTPS/JSON | RBAC, dashboards |
| Workshop View UI | Live Updates | Bidirectional | WebSocket/JSON | Low latency, optimized payloads |
| Notification Service | Notifications API | Outbound | REST/JSON | Customer updates |

### Example Payloads

**Appointment imported from planning:**

```json
{
  "appointmentId": "A-10293",
  "plate": "12-AB-34",
  "start": "2026-01-12T09:00:00+01:00",
  "service": "OilChange",
  "customerRef": "C-4451"
}
```

**Workshop update from a mechanic:**

```json
{
  "workOrderId": "WO-7781",
  "status": "WaitingForParts",
  "note": "Brake pads not in stock",
  "updatedBy": "mechanic-17",
  "updatedAt": "2026-01-12T10:41:00+01:00"
}
```

### Scope Boundary

```plantuml
@startuml
skinparam shadowing false
skinparam componentStyle rectangle

rectangle "Outside Pitstop" {
  rectangle "Planning Service"
  rectangle "Notification Service\n(optional)"
  rectangle "Inventory/Parts System\n(optional)"
}

rectangle "Pitstop (inside boundary)" {
  rectangle "Work Order Domain"
  rectangle "Sync & Integration Layer"
  rectangle "Admin Overview UI"
  rectangle "Workshop View UI"
}

"Planning Service" --> "Sync & Integration Layer" : appointments
"Sync & Integration Layer" --> "Planning Service" : status updates
"Work Order Domain" --> "Admin Overview UI" : dashboards
"Work Order Domain" --> "Workshop View UI" : task board
"Sync & Integration Layer" --> "Notification Service\n(optional)" : notify
"Work Order Domain" --> "Inventory/Parts System\n(optional)" : parts status reference
@enduml
```
