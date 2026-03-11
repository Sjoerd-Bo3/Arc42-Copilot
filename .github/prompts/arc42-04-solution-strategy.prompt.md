---
mode: 'ask'
description: 'Generate arc42 Chapter 4: Solution Strategy'
---

# Generate arc42 Chapter 4: Solution Strategy

I am working on arc42 architecture documentation.
Please help me write **Chapter 4: Solution Strategy** for `docs/arc42/arc42-template.md`.

## Context questions

Please ask me:

1. **What is the overall architectural style?** (e.g. microservices, modular monolith, event-driven, layered)
2. **What are the key technology choices?** (e.g. language, framework, cloud platform, database)
3. **How is the system decomposed at the top level?** (e.g. frontend/backend/services split)
4. **What integration approach is used?** (e.g. synchronous REST, async messaging, event streaming)
5. **How do the strategies address the quality goals from Chapter 1?** (map strategies to goals)
6. **Are there important trade-offs?** (e.g. consistency vs. availability, simplicity vs. scalability)

## Output format

Generate Markdown content ready to replace the placeholder in Chapter 4.

Structure:
- A brief paragraph summarizing the architectural philosophy (1–2 sentences)
- A table: Strategy | Decision / Approach | Rationale (links to ADRs in Ch9 if applicable)

## Tips

- Focus on the *why* — explain why each strategy was chosen given the context and constraints.
- This chapter should align with quality goals (Ch1) and constraints (Ch2).
- Keep it high-level: details belong in Ch5 (building blocks) and Ch9 (decisions).
- A new team member should understand the architecture direction after reading this.
- If a decision deserves a detailed write-up, link to an ADR in Chapter 9.
