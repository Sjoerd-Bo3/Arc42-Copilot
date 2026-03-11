# Arc42-Copilot

An opinionated arc42 architecture documentation toolkit with PlantUML diagrams, best practices, and AI-assisted iterative writing.

Inspired by the [arc42 practical blog series](https://blog.hompus.nl/2026/02/01/arc42-practical-series/) by Michael Hompus and the [Pitstop example](https://gist.github.com/eNeRGy164/90f63e78d3e528f7b8490538a6781b5f).

## What's included

| Folder | Description |
|--------|-------------|
| `templates/arc42-template/` | Copy-paste arc42 markdown template with PlantUML diagram stubs for every chapter |
| `templates/arc42-best-practices/` | Alternate template with embedded tips, anti-patterns, checklists, and guidance per section |
| `examples/pitstop/` | Fully worked-out Pitstop garage management example (all 12 chapters + PlantUML) |
| `.github/skills/` | Copilot skills for iteratively writing arc42 documentation |
| `.github/copilot-instructions.md` | Repository-wide Copilot instructions |

## Quick start

1. **New project** - Copy `templates/arc42-template/` into your repo's `docs/arc42/` folder.
2. **Need guidance** - Use `templates/arc42-best-practices/` instead for inline tips.
3. **See an example** - Browse `examples/pitstop/` for a complete, realistic reference.
4. **Write with AI** - Use the skills below with GitHub Copilot Chat or Claude.

## Skills

### Task skills (invoke with `/skill-name`)

| Skill | Purpose |
|-------|---------|
| `/arc42-scaffold` | Generate initial arc42 skeleton for a new project |
| `/arc42-chapter 5` | Write or improve a specific chapter |
| `/arc42-review` | Review docs for completeness and cross-chapter consistency |
| `/arc42-adr` | Create Architecture Decision Records |
| `/arc42-diagram` | Generate/improve PlantUML diagrams |
| `/arc42-quality` | Write testable quality scenarios for Chapter 10 |

### Agent skills (for complex workflows)

| Skill | Purpose |
|-------|---------|
| `/arc42-architect` | Full workflow: discovery, skeleton, core views, quality, risks |
| `/arc42-reviewer` | Cross-chapter consistency and completeness review |
| `/arc42-diagram-expert` | PlantUML specialist with patterns for every diagram type |

## PlantUML

All diagrams use [PlantUML](https://plantuml.com/) syntax embedded in markdown fenced code blocks. To render:

- **VS Code**: Install the [PlantUML extension](https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml)
- **GitHub**: Use a PlantUML proxy or GitHub Actions to render PNGs
- **CLI**: `plantuml -tpng docs/arc42/*.md`

## Iterative writing approach

Architecture documentation is never "done". The skills are designed for iterative use:

1. **Scaffold** - `/arc42-scaffold` to generate the initial structure
2. **Prioritize** - Write Ch1 (Goals), Ch3 (Context), Ch12 (Glossary) first
3. **Draft** - `/arc42-chapter` for each chapter, using codebase analysis
4. **Visualize** - `/arc42-diagram` to add/improve PlantUML diagrams
5. **Decide** - `/arc42-adr` when you make important architecture decisions
6. **Review** - `/arc42-review` to check consistency periodically
7. **Repeat** - Revisit docs when the architecture evolves

## Credits

- [arc42](https://arc42.org/) - The architecture documentation template
- [Michael Hompus](https://blog.hompus.nl/) - Practical arc42 blog series and Pitstop example
- [PlantUml.Builder](https://github.com/eNeRGy164/PlantUml.Builder) - PlantUML tooling reference
