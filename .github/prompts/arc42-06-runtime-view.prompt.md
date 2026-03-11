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
- A **PlantUML sequence diagram** using `participant`, `->`, `-->`, and `par` blocks where applicable
- Note any error handling or alternative paths

Use `plantuml` fenced code blocks. See `docs/arc42/pitstop-example.md` Chapter 6 for reference examples including parallel flows and error scenarios.

## Tips

- Pick scenarios that illustrate non-obvious interactions — skip trivial CRUD.
- Include at least one error/failure scenario.
- Use component names from Chapter 5 for consistency.
- Do NOT repeat the static structure from Ch5 here — focus on the "what happens when".
- Use `par` blocks in PlantUML to show parallel fan-out to multiple services.
- Example PlantUML sequence:
  ```plantuml
  @startuml scenario-name
  !theme plain
  participant "User" as User
  participant "API" as API
  participant "Service" as Service
  User -> API : POST /orders
  API -> Service : createOrder(data)
  Service --> API : OrderCreated event
  API --> User : 201 Created
  @enduml
  ```
