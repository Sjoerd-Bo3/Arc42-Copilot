---
mode: 'ask'
description: 'Generate arc42 Chapter 5: Building Block View'
---

# Generate arc42 Chapter 5: Building Block View

I am working on arc42 architecture documentation.
Please help me write **Chapter 5: Building Block View** for `docs/arc42/arc42-template.md`.

## Context questions

Please ask me:

1. **What are the top-level components or services of the system?** (name and 1-sentence responsibility for each)
2. **How do the components communicate?** (synchronous calls, async messages, shared database, etc.)
3. **Are there any components that warrant deeper decomposition?** If so, what are their sub-components?
4. **What are the key interfaces between components?** (APIs, message contracts, shared libraries)
5. **Are there any external dependencies at the component level?** (databases, caches, message brokers)

## Output format

Generate Markdown content ready to replace the placeholder in Chapter 5.

Structure:
- 5.1 Level 1 — Top-Level Decomposition:
  - A **PlantUML component diagram** using `component`, `queue`, `database` elements
  - A table: Building Block | Responsibility | Key Interfaces / Dependencies
- 5.2+ Level 2 — for any components that need detail (one subsection per complex component, also with a PlantUML diagram)

Use `plantuml` fenced code blocks. See `docs/arc42/pitstop-example.md` Chapter 5 for reference examples.

## Tips

- Describe WHAT each block does, not HOW it does it internally.
- Match the component names to the actual code structure (folders, services, namespaces).
- Do NOT describe behavior/flows here — that is for Chapter 6 (Runtime View).
- Keep the diagram simple: too many boxes and arrows obscures understanding.
- Align components with team boundaries where possible (team A owns component A).
- If using C4 model, this corresponds to the Container diagram (Level 1) and Component diagrams (Level 2).
