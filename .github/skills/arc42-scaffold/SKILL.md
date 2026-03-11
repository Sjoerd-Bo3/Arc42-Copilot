---
name: arc42-scaffold
description: Generate the initial arc42 documentation skeleton for a new project. Creates all 12 chapters with PlantUML diagram stubs.
argument-hint: "project name and one-line description"
---

# Arc42 Scaffold Generator

Generate a complete arc42 skeleton based on the user's project description.

## What you need from the user

Ask if not provided:
1. **Project name** and one-line description
2. **Problem statement** — what problem does this system solve?
3. **Key stakeholders** — who uses or depends on this system?
4. **Known constraints** — platform, technology, compliance requirements

## What you produce

Generate all 12 arc42 chapters as separate markdown files in `docs/arc42/`. For each chapter:

- Fill in section headers and tables
- Add PlantUML diagram stubs with placeholder components named after the user's domain
- Mark sections that need more information with `<!-- TODO: ... -->`
- Use the project name consistently throughout

Use `templates/arc42-template/` as the structural reference and `templates/arc42-best-practices/` for guidance on what belongs in each section.

## PlantUML conventions

Always apply these settings in every diagram:

```plantuml
skinparam shadowing false
skinparam componentStyle rectangle
```

Color coding:
| Element | Color |
|---------|-------|
| Your system (boundary) | `#LightBlue` |
| Main system in context diagrams | `#OrangeRed` |
| Infrastructure | `#lightgreen` |
| External systems | `#lightblue` |

## Quality checks

- Every placeholder should be actionable (not "fill this in" but "describe the retry strategy for vendor X")
- Quality goals in Ch1 must be ranked
- Non-goals should be included in Ch1
- Glossary (Ch12) should contain at least the key domain terms
