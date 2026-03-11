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

Use Mermaid syntax for diagrams when possible. Acceptable formats:
- `graph TD` or `flowchart TD` for component/context diagrams
- `sequenceDiagram` for runtime view scenarios
- `graph LR` for deployment overviews

Alternatively, ASCII art diagrams are acceptable for simple structures.

## Commit message convention

When committing changes to arc42 documentation, prefix with `docs(arc42):`.
Example: `docs(arc42): add chapter 1 introduction and quality goals`
