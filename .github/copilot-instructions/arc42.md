# Arc42 Copilot Instructions

## Context

This repository contains arc42 architecture documentation templates, best practices, and AI-assisted tooling for writing architecture docs iteratively.

## Available Prompts

Use these prompts with GitHub Copilot Chat (`@workspace` or file references):

| Prompt | Purpose | When to use |
|--------|---------|-------------|
| `arc42-scaffold` | Generate initial arc42 skeleton | Starting a new project |
| `arc42-chapter-writer` | Write/improve a specific chapter | Filling in chapters iteratively |
| `arc42-review` | Review docs for completeness/consistency | After writing multiple chapters |
| `arc42-adr-writer` | Create Architecture Decision Records | When documenting a decision |
| `arc42-plantuml-diagrams` | Generate PlantUML diagrams | When adding/improving visuals |
| `arc42-quality-scenarios` | Write testable quality scenarios | When working on Chapter 10 |

## Available Agents

| Agent | Purpose |
|-------|---------|
| `arc42-architect` | Full workflow: discovery → skeleton → core views → quality |
| `arc42-reviewer` | Cross-chapter consistency and completeness review |
| `arc42-diagram-expert` | PlantUML diagram creation and improvement |

## Iterative Workflow

Architecture documentation is never "done". Use this workflow:

1. **Start**: Use `arc42-scaffold` to generate the skeleton
2. **Prioritize**: Write Ch1 (Goals), Ch3 (Context), Ch12 (Glossary) first
3. **Iterate**: Use `arc42-chapter-writer` for each chapter
4. **Visualize**: Use `arc42-plantuml-diagrams` to add/improve diagrams
5. **Decide**: Use `arc42-adr-writer` when you make important decisions
6. **Review**: Use `arc42-review` periodically to check consistency
7. **Repeat**: Architecture evolves — revisit docs when the system changes

## PlantUML Conventions

- Always use `skinparam shadowing false` and `skinparam componentStyle rectangle`
- Color code: `#LightBlue` (your system), `#lightgreen` (infra), `#lightblue` (external)
- Sequence diagrams: `hide footbox`, use `++`/`--` for activation
- Max 7-10 elements per diagram
- Every arrow needs a label

## Reference

- Templates: `templates/arc42-template/` (clean) and `templates/arc42-best-practices/` (guided)
- Example: `examples/pitstop/` (fully worked-out Pitstop garage management system)
- Blog series: https://blog.hompus.nl/2026/02/01/arc42-practical-series/
