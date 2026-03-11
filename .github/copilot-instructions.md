# Arc42-Copilot Instructions

This repository provides arc42 architecture documentation templates, best practices, and AI-assisted skills for writing docs iteratively.

## Repository structure

| Folder | Description |
|--------|-------------|
| `templates/arc42-template/` | Clean copy-paste arc42 skeleton with PlantUML stubs |
| `templates/arc42-best-practices/` | Guided template with tips, anti-patterns, and checklists |
| `examples/pitstop/` | Fully worked-out Pitstop garage management example |

## Available skills

### Task skills (user-invocable)

| Skill | Slash command | Purpose |
|-------|--------------|---------|
| `arc42-scaffold` | `/arc42-scaffold` | Generate initial arc42 skeleton for a new project |
| `arc42-chapter` | `/arc42-chapter 5` | Write or improve a specific chapter |
| `arc42-review` | `/arc42-review` | Review docs for completeness and consistency |
| `arc42-adr` | `/arc42-adr` | Create Architecture Decision Records |
| `arc42-diagram` | `/arc42-diagram` | Generate/improve PlantUML diagrams |
| `arc42-quality` | `/arc42-quality` | Write testable quality scenarios |

### Agent skills (for complex workflows)

| Skill | Purpose |
|-------|---------|
| `arc42-architect` | Full workflow: discovery, skeleton, views, quality, risks |
| `arc42-reviewer` | Cross-chapter consistency and completeness review |
| `arc42-diagram-expert` | PlantUML specialist with patterns for every diagram type |

## Iterative writing workflow

Architecture documentation is never "done". Recommended order:

1. `/arc42-scaffold` — Generate the initial structure
2. Write Ch1 (Goals), Ch3 (Context), Ch12 (Glossary) first
3. `/arc42-chapter` — Fill in each chapter from codebase
4. `/arc42-diagram` — Add/improve PlantUML diagrams
5. `/arc42-adr` — Document important decisions
6. `/arc42-review` — Check consistency periodically
7. Repeat as the architecture evolves

## PlantUML conventions

All diagrams in this repo use consistent PlantUML styling:

- `skinparam shadowing false` and `skinparam componentStyle rectangle`
- Colors: `#LightBlue` (your system), `#OrangeRed` (emphasis), `#lightgreen` (infra), `#lightblue` (external)
- Sequence diagrams: `hide footbox`, `++`/`--` activation
- Max 7-10 elements per diagram, every arrow labeled

## Reference

- [arc42.org](https://arc42.org/) — The official arc42 template
- [Blog series](https://blog.hompus.nl/2026/02/01/arc42-practical-series/) — Practical arc42 by Michael Hompus
- [Pitstop gist](https://gist.github.com/eNeRGy164/90f63e78d3e528f7b8490538a6781b5f) — Complete example
