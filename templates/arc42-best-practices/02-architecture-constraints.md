# 2. Architecture Constraints

> **Purpose**: Document the non-negotiable boundaries. These are things you *cannot* change — they were decided before you arrived or are imposed by the environment.

| Constraint | Type | Rationale | Impact on architecture |
|------------|------|-----------|----------------------|
| | Technical | | |
| | Organizational | | |
| | Convention | | |

> **Tip**: Types of constraints:
> - **Technical**: "Must run on Azure", "Must use PostgreSQL", "API must be REST"
> - **Organizational**: "Team of 3 developers", "No budget for commercial licenses", "Must ship by Q3"
> - **Conventions**: "All services must follow OpenAPI spec", "ADRs required for deviations"

> **Anti-pattern**: Confusing constraints with decisions. A constraint is imposed on you. A decision is something you chose. If you could have picked differently, it belongs in Chapter 4 (Solution Strategy) or Chapter 9 (ADRs).

> **Anti-pattern**: Listing things that are obviously true ("must be secure", "must work"). Only list constraints that actually limit your design space.

## Completion Checklist

- [ ] Each constraint explains *who* imposed it and *why*
- [ ] Each constraint has a concrete impact on the architecture
- [ ] Constraints are not disguised decisions
- [ ] There are no "obvious" entries that don't actually constrain anything
