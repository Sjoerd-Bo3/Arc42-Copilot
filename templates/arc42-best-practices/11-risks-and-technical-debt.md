# 11. Risks and Technical Debt

> **Purpose**: Be honest about what could go wrong and what shortcuts you took. This chapter builds trust — it shows you've thought about failure modes.

## Risks

<!-- Phrase as: "What could hurt us?" + "What we'll do about it" -->

| Risk | Why it matters | Mitigation |
|------|---------------|------------|
| | | |

> **Tip**: Good risks are specific. "Security breach" is too vague. "Leaked API key allows unauthorized access to planning vendor" is actionable.

> **Tip**: Include integration risks (vendor goes down, API changes), operational risks (network flaky), and organizational risks (key person leaves).

## Known Technical Debt (intentional)

<!-- Debt you chose to take on. Document WHY it was acceptable and WHEN to revisit. -->

| Debt item | Rationale (why acceptable now) | Revisit when |
|-----------|-------------------------------|-------------|
| | | |

> **Tip**: Intentional debt is fine — undocumented debt is dangerous. If you know something is a shortcut, write it down so the team can plan for it.

> **Anti-pattern**: Pretending there are no risks. Every system has them. An empty risk table signals denial, not quality.

> **Anti-pattern**: Risks without mitigations. A risk list without "what we'll do about it" is just a worry list.

## Completion Checklist

- [ ] At least 3-5 concrete, specific risks are listed
- [ ] Every risk has a mitigation strategy
- [ ] Known technical debt is documented with rationale
- [ ] Debt items have a "revisit when" trigger
- [ ] Risks cover integration, operational, and organizational categories
