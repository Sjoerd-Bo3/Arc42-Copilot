---
applyTo: 'docs/arc42/**'
---

# Arc42 Documentation Instructions

When working with files in `docs/arc42/`:

## Required structure

All files must follow the arc42 12-chapter structure. The main template is `arc42-template.md`.

## Content rules

- Each chapter heading must use the exact arc42 chapter titles (e.g. "## 1. Introduction and Goals").
- Chapter sections must be numbered consistently (e.g. "### 1.1 Requirements Overview").
- Placeholder text uses italic brackets: `_[description of what goes here]_`.
- Completed sections remove the placeholder and contain real content.

## Quality standards

- **Quality goals must be measurable:** "P95 response time < 200ms" ✓ | "fast" ✗
- **Architectural decisions must include rationale** and alternatives considered.
- **Constraints must include background** explaining why the constraint exists.
- **Component names must be consistent** across all chapters (Chapters 3, 5, 6, 7).

## Diagrams

**Preferred format: PlantUML** — use a `plantuml` fenced code block.
See `pitstop-example.md` for real examples of each diagram type.

Common PlantUML diagram types:
- `@startuml` with `actor`, `rectangle`, `component` for context and building block views
- `@startuml` with `participant`, `->`, `-->` for sequence diagrams (runtime view)
- `@startuml` with `node`, `rectangle`, `database` for deployment diagrams

Mermaid (`flowchart TD`, `sequenceDiagram`) is also acceptable when PlantUML is not practical.
ASCII art is acceptable only for very simple placeholder structures during early drafts.

## Commit message convention

When committing changes to arc42 documentation, prefix with `docs(arc42):`.
Example: `docs(arc42): add chapter 1 introduction and quality goals`
