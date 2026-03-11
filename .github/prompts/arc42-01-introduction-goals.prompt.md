---
mode: 'ask'
description: 'Generate arc42 Chapter 1: Introduction and Goals'
---

# Generate arc42 Chapter 1: Introduction and Goals

I am working on arc42 architecture documentation for a software system.
Please help me write **Chapter 1: Introduction and Goals** for the file `docs/arc42/arc42-template.md`.

## What I need you to know about the system

Before generating content, please ask me the following questions (one at a time or all at once):

1. **What is the system called?** What is its primary purpose in 1–2 sentences?
2. **What problem does it solve?** What pain or need does it address?
3. **Who are the key stakeholders?** (e.g. end users, product owner, operations team, customers)
4. **What are the top 3–5 quality goals?** (e.g. availability, performance, security, modifiability)
5. **What are the most important requirements?** (bullet points, not exhaustive)
6. **What are the explicit non-goals?** What does the system intentionally NOT do?

## Output format

Generate the content as Markdown, ready to replace the placeholder text in Chapter 1 of the arc42 template.

Follow this structure:
- A short introduction paragraph (1–3 sentences) describing the system, the problem, and the context.
- Section 1.1: Requirements overview (key requirements + explicit non-goals as bullet lists)
- Section 1.2: Quality goals as a table with columns: Priority, Quality Goal, Scenario, Acceptance Criteria
- Section 1.3: Stakeholders as a table with columns: Stakeholder, Role / Interest, Key Expectations

## Tips for great Chapter 1 content

- Quality goals must be **measurable**, not vague (e.g. "P95 response time < 200ms" not "fast").
- Keep the requirements list short — 5–10 items max. Leave out the obvious.
- Stakeholders should include anyone who has an interest in the architecture, not just end users.
- If you only write one chapter perfectly, make it this one.
