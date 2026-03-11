# Arc42-Copilot

An opinionated arc42 architecture documentation toolkit with PlantUML diagrams, best practices, and AI-assisted iterative writing.

Inspired by the [arc42 practical blog series](https://blog.hompus.nl/2026/02/01/arc42-practical-series/) by Michael Hompus and the [Pitstop example](https://gist.github.com/eNeRGy164/90f63e78d3e528f7b8490538a6781b5f).

## What's included

| Folder | Description |
|--------|-------------|
| `templates/arc42-template/` | Copy-paste arc42 markdown template with PlantUML diagram stubs for every chapter |
| `templates/arc42-best-practices/` | Alternate template with embedded tips, anti-patterns, checklists, and guidance per section |
| `examples/pitstop/` | Fully worked-out Pitstop garage management example (all 12 chapters + PlantUML) |
| `.github/prompts/` | GitHub Copilot prompt files for iteratively writing each arc42 chapter |
| `copilot-agents/` | Copilot Chat agent definitions for architecture documentation workflows |

## Quick start

1. **New project** - Copy `templates/arc42-template/` into your repo's `docs/arc42/` folder.
2. **Need guidance** - Use `templates/arc42-best-practices/` instead for inline tips.
3. **See an example** - Browse `examples/pitstop/` for a complete, realistic reference.
4. **Write with AI** - Use the prompts in `.github/prompts/` with GitHub Copilot Chat or Claude.

## PlantUML

All diagrams use [PlantUML](https://plantuml.com/) syntax embedded in markdown fenced code blocks. To render:

- **VS Code**: Install the [PlantUML extension](https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml)
- **GitHub**: Use a PlantUML proxy or GitHub Actions to render PNGs
- **CLI**: `plantuml -tpng docs/arc42/*.md`

## Iterative writing approach

Architecture documentation is never "done". The prompts and agents are designed for iterative use:

1. **Skeleton** - Generate the initial structure with placeholders
2. **Draft** - Fill in each chapter using the guided prompts
3. **Review** - Use the review agent to check completeness and consistency
4. **Refine** - Iterate on specific sections as the architecture evolves

## Credits

- [arc42](https://arc42.org/) - The architecture documentation template
- [Michael Hompus](https://blog.hompus.nl/) - Practical arc42 blog series and Pitstop example
- [PlantUml.Builder](https://github.com/eNeRGy164/PlantUml.Builder) - PlantUML tooling reference
