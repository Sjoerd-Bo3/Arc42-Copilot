# 4. Solution Strategy

Pitstop is designed as an operational "source of truth" for work orders and status, with near real-time synchronization between planning and workshop execution.

## Core Decisions

| Decision | Quality Goal | Rationale |
|----------|-------------|-----------|
| Modular monolith backend (initially) | Modifiability | Keep deployment simple while domain stabilizes. Modules communicate via explicit interfaces. |
| Adapter-based integrations | Modifiability | Each external system behind a port/adapter boundary. New integrations in 2 days. |
| Near real-time updates via push | Consistency | Workshop and admin need shared truth in 2 seconds. WebSocket/SSE with polling fallback. |
| Degraded-mode workshop operation | Availability | Workshop UI supports local queueing and later sync when connectivity returns. |
| Audit-first changes | Auditability | Every status change records who/when/why in immutable history. |

## Open Strategy Questions

| Question | Affects | Status |
|----------|---------|--------|
| WebSocket vs SSE as default push channel? | Real-time UX, infra constraints | Open |
| Conflict resolution approach after offline edits? | User trust, operational continuity | Open |
