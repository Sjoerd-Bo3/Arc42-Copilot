# 2. Architecture Constraints

| Constraint | Type | Rationale | Impact |
|------------|------|-----------|--------|
| Must integrate with Planning Service(s) | Integration | Existing ecosystem reality | API contracts, sync strategy, mapping rules |
| Near real-time UI updates | UX/Operational | Workshop coordination | Push updates (WebSocket) or efficient polling |
| Degraded-mode operation | Operational | Garage networks can be unreliable | Local cache/queue, retry, conflict handling |
| Containerized deployment | Platform | Standard ops model | Registry, base images, runtime policy |
| Automated CI + tests | Process | Fast feedback and reliability | Pipeline ownership + test environments |
| GDPR / minimal personal data | Compliance | Customer data | Data minimization, retention rules, audit controls |
| Deviations recorded as ADRs | Governance | Prevent silent divergence | ADR workflow (see Chapter 9) |
