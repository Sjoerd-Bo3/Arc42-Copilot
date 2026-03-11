---
mode: 'ask'
description: 'Generate arc42 Chapter 6: Runtime View'
---

# Generate arc42 Chapter 6: Runtime View

I am working on arc42 architecture documentation.
Please help me write **Chapter 6: Runtime View** for `docs/arc42/arc42-template.md`.

## Context questions

Please ask me:

1. **What are the 2–5 most critical use cases or flows in the system?**
2. **For each scenario: what is the trigger?** (user action, scheduled job, external event)
3. **For each scenario: which components are involved?** (refer to building blocks from Ch5)
4. **For each scenario: what is the sequence of interactions?** (step by step)
5. **Are there important error or failure scenarios?** (e.g. downstream service unavailable, data validation failure)
6. **Are there important performance-critical paths?** (flows where latency matters most)

## Output format

Generate Markdown content ready to replace the placeholder in Chapter 6.

For each scenario:
- A brief title and description (1–2 sentences)
- A Mermaid sequence diagram or numbered step-by-step list showing the interaction
- Note any error handling or alternative paths

## Tips

- Pick scenarios that illustrate non-obvious interactions — skip trivial CRUD.
- Include at least one error/failure scenario.
- Use component names from Chapter 5 for consistency.
- Do NOT repeat the static structure from Ch5 here — focus on the "what happens when".
- Sequence diagrams are ideal for showing timing and order of interactions.
- Example Mermaid sequence:
  ```
  sequenceDiagram
    participant User
    participant API
    participant Service
    User->>API: POST /orders
    API->>Service: createOrder(data)
    Service-->>API: OrderCreated event
    API-->>User: 201 Created
  ```
