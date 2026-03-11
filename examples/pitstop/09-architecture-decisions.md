# 9. Architecture Decisions

| Date | Decision | Status |
|------|----------|--------|
| 2026-01-24 | [ADR-001 Modular monolith backend (initially)](#adr-001-modular-monolith-backend-initially) | Accepted |
| 2026-01-18 | [ADR-002 Add degraded mode for workshop updates](#adr-002-add-degraded-mode-for-workshop-updates) | Accepted |

## ADR-001: Modular monolith backend (initially)

- **Status:** Accepted
- **Date:** 2026-01-24

### Context

Pitstop needs to ship quickly, integrate with multiple planning vendors, and evolve domain rules fast. The system must remain easy to deploy for small garages and still be maintainable for larger chains.

### Decision

Build the backend as a **modular monolith**: one deployable backend with clear internal module boundaries (Work Orders, Workshop, Scheduling Sync, Audit) and integrations behind ports/adapters.

### Consequences

- Easier deployment and debugging (one runtime)
- Faster iteration while domain is still moving
- Module boundaries prepare for future extraction if needed
- Requires discipline to prevent "big ball of mud" (enforce boundaries, tests, and ADRs)

## ADR-002: Add degraded mode for workshop updates

- **Status:** Accepted
- **Date:** 2026-01-18

### Context

Workshop connectivity is not reliable in every garage. Status updates must remain possible during outages, and the system must recover safely.

### Decision

Pitstop supports **a degraded mode where the workshop UI can keep working while offline**. Updates are queued locally and replayed later with idempotency keys to prevent double-apply.

### Consequences

- Workshop UI becomes stateful and needs conflict handling
- Backend needs idempotency storage and replay rules
- Improved availability in unreliable network conditions

### Considered Alternatives

1. **Reject updates when offline** — rejected because it blocks the workshop and causes lost work.
2. **Full offline-first architecture** — rejected as over-engineering for the current scale.
