# 9. Architecture Decisions

> **Purpose**: Record important decisions and their context so future team members understand *why* things are the way they are.

> **When to write an ADR**:
> - Choosing between significant alternatives (framework, pattern, protocol)
> - Deviating from a constraint or convention
> - Making a trade-off that future developers might question

> **ADR lifecycle**: Proposed → Accepted → Deprecated / Superseded

| Date | Decision | Status |
|------|----------|--------|
| YYYY-MM-DD | [ADR-001 Title](#adr-001-title) | Accepted |

## ADR-001: «Title»

- **Status:** Proposed
- **Date:** YYYY-MM-DD

### Context

<!-- What forces are at play? What problem are you solving? What constraints apply? -->

### Decision

<!-- State the decision clearly. "We will use X for Y." -->

### Consequences

<!-- What becomes easier? What becomes harder? Be honest about trade-offs. -->

- Positive consequence
- Negative consequence / risk

### Considered Alternatives

<!-- What did you reject and why? This is often the most valuable part. -->

1. **Alternative A** — rejected because...
2. **Alternative B** — rejected because...

> **Tip**: The "Considered Alternatives" section is the most valuable part. It prevents the next developer from re-evaluating options you already rejected.

> **Tip**: Keep ADRs immutable. If a decision changes, create a new ADR that supersedes the old one. Don't edit history.

> **Anti-pattern**: ADRs without context. "We chose PostgreSQL" without explaining *why* and *what else was considered* is useless.

> **Anti-pattern**: Only documenting "good" decisions. The most useful ADRs explain trade-offs and known limitations.

## Completion Checklist

- [ ] Every significant architecture decision has an ADR
- [ ] Each ADR has context, decision, consequences, and alternatives
- [ ] ADRs are immutable (superseded, not edited)
- [ ] New team members can understand the "why" from ADRs alone
