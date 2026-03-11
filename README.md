# Arc42-Copilot

A practical arc42 architecture documentation template with GitHub Copilot prompts, agents, and instructions to help you write and maintain architecture documentation iteratively.

> Inspired by Michaël Hompus's [Arc42 Practical Series](https://blog.hompus.nl/2026/02/01/arc42-practical-series/) and the [arc42 template](https://arc42.org/).

---

## What's included

| File / Directory | Description |
| :--- | :--- |
| `docs/arc42/arc42-template.md` | The arc42 template with best practices, tips, and "done-when" criteria for all 12 chapters |
| `.github/copilot-instructions.md` | Repository-wide GitHub Copilot instructions for arc42 documentation standards |
| `.github/instructions/arc42.instructions.md` | File-scoped instructions applied to all files in `docs/arc42/` |
| `.github/agents/arc42-documentation-agent.md` | A dedicated GitHub Copilot agent for iterative arc42 documentation sessions |
| `.github/prompts/arc42-01-*.prompt.md` … `arc42-12-*.prompt.md` | Reusable Copilot prompts — one per arc42 chapter |
| `.github/prompts/arc42-review.prompt.md` | Prompt to review your arc42 documentation for completeness and consistency |
| `.github/prompts/arc42-full-session.prompt.md` | Prompt to run a full iterative documentation session across multiple chapters |

---

## Getting started

### Option A: Use the arc42 agent (recommended)

1. Open GitHub Copilot Chat in VS Code.
2. Switch to **Agent mode** and select `arc42-documentation-agent`.
3. Start a session — the agent will guide you through the documentation iteratively.

### Option B: Use individual chapter prompts

1. Open the relevant prompt file (e.g. `.github/prompts/arc42-01-introduction-goals.prompt.md`) in VS Code.
2. Click **Run Prompt** (or use `@workspace` with the prompt content in Copilot Chat).
3. Answer the context questions and get a draft for that chapter.
4. Paste the generated content into `docs/arc42/arc42-template.md`.

### Option C: Write manually with AI assistance

1. Open `docs/arc42/arc42-template.md`.
2. GitHub Copilot will automatically apply the instructions from `.github/copilot-instructions.md`.
3. Use inline Copilot suggestions as you write each section.

---

## The arc42 template structure

The template covers all 12 arc42 chapters, with best practices and "done-when" criteria embedded in each section:

1. **Introduction and Goals** — Why are we building this? For whom?
2. **Architecture Constraints** — What limits our design choices?
3. **System Scope and Context** — What is inside and outside the system?
4. **Solution Strategy** — What are the big architectural decisions?
5. **Building Block View** — What are the static components and their relationships?
6. **Runtime View** — How does the system behave in key scenarios?
7. **Deployment View** — Where does the system run?
8. **Cross-Cutting Concepts** — What overarching patterns apply everywhere?
9. **Architectural Decisions** — What key decisions were made and why?
10. **Quality Requirements** — How are quality goals measured and tested?
11. **Technical Risks and Debts** — What can bite us later?
12. **Glossary** — What do the key terms mean?

---

## Philosophy: Start small, iterate often

This template follows the pragmatic approach from Hompus's practical series:

- **Start with Chapter 1.** If you only write one chapter, make it the Introduction and Goals.
- **Document what matters.** Skip sections that don't add value for your system.
- **Iterate over time.** Update the docs when the architecture changes — treat them like code.
- **Keep it close to the code.** Store the docs in your repository so they are versioned and reviewed.

---

## References

- [arc42 — The Template for Software Architecture Documentation](https://arc42.org/)
- [Arc42 Practical Series by Michaël Hompus](https://blog.hompus.nl/2026/02/01/arc42-practical-series/)
- [arc42 template on GitHub](https://github.com/arc42/arc42-template)
