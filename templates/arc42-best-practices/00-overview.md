# Architecture Documentation (arc42) — With Best Practices

> This is the **guided version** of the arc42 template. Each section includes tips, anti-patterns, and completion checklists.
> For the clean template without guidance, see `templates/arc42-template/`.

## The Minimal but Honest Rule

> Write the smallest amount of documentation that prevents expensive misunderstandings.
> — Michael Hompus, arc42 Practical Series

## Writing Order (recommended)

You don't have to write chapters in order. Start where the value is highest:

| Phase | Chapters | Why |
|-------|----------|-----|
| **Start here** | 1 (Goals), 3 (Context), 12 (Glossary) | Align stakeholders on scope and language |
| **Then** | 4 (Strategy), 2 (Constraints) | Lock in key decisions and boundaries |
| **Core views** | 5 (Building blocks), 6 (Runtime), 7 (Deployment) | The "what does it look like" chapters |
| **Cross-cutting** | 8 (Concepts), 9 (ADRs) | Patterns and decisions that span views |
| **Quality** | 10 (Quality), 11 (Risks) | Testable scenarios and honest risk assessment |

## Chapters

| # | Title | Status |
|---|-------|--------|
| 1 | [Introduction and Goals](01-introduction-and-goals.md) | Draft |
| 2 | [Architecture Constraints](02-architecture-constraints.md) | Draft |
| 3 | [Context and Scope](03-context-and-scope.md) | Draft |
| 4 | [Solution Strategy](04-solution-strategy.md) | Draft |
| 5 | [Building Block View](05-building-block-view.md) | Draft |
| 6 | [Runtime View](06-runtime-view.md) | Draft |
| 7 | [Deployment View](07-deployment-view.md) | Draft |
| 8 | [Crosscutting Concepts](08-crosscutting-concepts.md) | Draft |
| 9 | [Architecture Decisions](09-architecture-decisions.md) | Draft |
| 10 | [Quality Requirements](10-quality-requirements.md) | Draft |
| 11 | [Risks and Technical Debt](11-risks-and-technical-debt.md) | Draft |
| 12 | [Glossary](12-glossary.md) | Draft |

## Keeping Documentation Alive

- **Treat docs like code**: review in PRs, version with the source.
- **Assign ownership**: each chapter has an owner who keeps it current.
- **Review cadence**: check docs quarterly or after significant architecture changes.
- **Automate what you can**: generate deployment views from IaC, keep diagrams as PlantUML code.
- **Delete stale content**: outdated docs are worse than no docs.
