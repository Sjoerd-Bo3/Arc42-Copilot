# GitHub Copilot Instructions — Arc42 Architecture Documentation

This repository uses the **arc42** template for software architecture documentation.
When helping with documentation in this repository, follow these guidelines.

## Arc42 Documentation Standards

- All architecture documentation lives in `docs/arc42/arc42-template.md`.
- See `docs/arc42/pitstop-example.md` for a complete, filled-in example with PlantUML diagrams.
- Follow the arc42 12-chapter structure: Introduction & Goals, Constraints, Context, Solution Strategy, Building Blocks, Runtime, Deployment, Cross-Cutting Concepts, Decisions, Quality, Risks, Glossary.
- Keep documentation concise and focused — document what matters, skip what doesn't.
- Always explain the *why* behind decisions, not just the *what*.
- Quality goals must be **measurable** (e.g. "P95 < 500ms", not "fast").
- Architecture Decision Records (ADRs) should follow the format: date, decision, status, rationale, alternatives considered.

## Writing Style

- Use clear, plain language that both technical and non-technical stakeholders can understand.
- Prefer tables and bullet points over long prose for reference information (stakeholders, constraints, decisions).
- Keep each chapter self-contained enough to be read independently.

## Diagrams

- **Preferred format: PlantUML** — use a `plantuml` fenced code block (renders with VS Code extensions and GitHub Apps).
- See `docs/arc42/pitstop-example.md` for PlantUML examples of context diagrams, building block views, sequence diagrams, and deployment diagrams.
- Mermaid is acceptable as an alternative.
- Keep diagrams simple — too many boxes obscures understanding.

## Iterative Approach

- Start small: the first draft does not need to be complete.
- Fill in only what you know today — leave placeholders (`_[to be determined]_`) for unknown sections.
- Improve incrementally with each significant architecture change.

## Copilot Prompts

Reusable prompts for generating arc42 documentation are in `.github/prompts/`. Use them with `@workspace` or by opening them in Copilot Chat. Each prompt is designed for one arc42 chapter and will ask you for project-specific context before generating content.

## Agent

A dedicated documentation agent is defined in `.github/agents/arc42-agent.md`. Use it in Copilot agent mode for a focused documentation writing session.
