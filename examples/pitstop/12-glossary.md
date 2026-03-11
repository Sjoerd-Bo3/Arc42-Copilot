# 12. Glossary

## Terms and Abbreviations

| Term | Meaning |
|------|---------|
| **ADR** | Architecture Decision Record — captures an important decision, its context, and consequences |
| **Appointment** | A planned time slot in the Planning Service |
| **Work Order (WO)** | The operational "job" in Pitstop: tasks, status, notes, parts dependency, assignment |
| **Task / Job** | A unit of work within a work order (e.g., Oil change, Replace pads) |
| **Bay** | Physical workplace in the workshop (where cars are worked on) |
| **Foreman** | Workshop lead responsible for prioritization and bay allocation |
| **Degraded mode** | Workshop continues with limited connectivity (local queue + later sync) |
| **Outbox (local)** | Client-side queue storing commands while offline to replay later |
| **Idempotency key** | A unique key to ensure repeated messages are processed only once |
| **Audit event** | Immutable record of a meaningful change (who/when/why/what) |
| **RBAC** | Role-based access control — restricts access based on assigned roles |
| **Read model** | Projection optimized for dashboards/reporting (separate from write model) |
| **Planning Vendor** | External planning system providing appointments and receiving status updates |
| **ConnectivityMode** | Deployment setting that tunes online-first vs offline-first behavior |
| **Source of truth** | The system that owns the authoritative state. Planning owns appointments; Pitstop owns work order status. |
| **Status** | In Pitstop, always means work order status (lifecycle from `Created` to `Done`) |
| **SSE** | Server-sent events — server push over a single HTTP connection |
| **WS** | WebSocket — full-duplex communication over a single TCP connection |

## Translations

| English (docs) | Dutch (domain/UI) | Notes |
|----------------|------------------|-------|
| Work order | Werkorder | UI label used by garages |
| Workshop | Werkplaats | Used in training materials and onboarding |
