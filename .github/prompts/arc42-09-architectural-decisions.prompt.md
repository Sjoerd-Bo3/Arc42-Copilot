---
mode: 'ask'
description: 'Generate arc42 Chapter 9: Architectural Decisions (ADR)'
---

# Generate arc42 Chapter 9: Architectural Decisions

I am working on arc42 architecture documentation.
Please help me write **Chapter 9: Architectural Decisions** for `docs/arc42/arc42-template.md`.

## Context questions

Please ask me:

1. **What are the most significant architectural decisions made so far?**
2. **For each decision: what was decided?** (the outcome)
3. **For each decision: when was it made?** (approximate date)
4. **For each decision: why was it made?** (the driver — quality goal, constraint, pragmatism)
5. **For each decision: what alternatives were considered and why rejected?**
6. **What is the current status?** (Accepted / Proposed / Deprecated / Superseded)

## Output format

Generate Markdown content ready to replace the placeholder in Chapter 9.

Structure:
- A summary table: Date | Decision | Status | Rationale / Alternatives Considered
- For any complex decision that deserves detail, a full ADR sub-section below the table:

```markdown
### ADR-001: [Decision Title]

**Date:** YYYY-MM-DD
**Status:** Accepted

**Context:**
[Why was this decision needed? What is the problem being solved?]

**Decision:**
[What was decided?]

**Rationale:**
[Why this option? What drivers influenced it?]

**Alternatives Considered:**
- [Alternative 1]: [Why rejected]
- [Alternative 2]: [Why rejected]

**Consequences:**
- [Positive or negative outcomes of this decision]
```

## Tips

- Focus on decisions with significant, long-lasting impact — not every design choice.
- Skip decisions that are easily reversed or trivially obvious.
- The table gives a quick overview; ADR sub-sections give depth for important decisions.
- This chapter should grow over time — new decisions get added, old ones get "Superseded" status.
- Linking decisions to quality goals and constraints from earlier chapters shows coherent reasoning.
- ADR status values: Proposed | Accepted | Deprecated | Superseded by ADR-xxx
