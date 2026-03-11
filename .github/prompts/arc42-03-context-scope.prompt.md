---
mode: 'ask'
description: 'Generate arc42 Chapter 3: System Scope and Context'
---

# Generate arc42 Chapter 3: System Scope and Context

I am working on arc42 architecture documentation.
Please help me write **Chapter 3: System Scope and Context** for `docs/arc42/arc42-template.md`.

## Context questions

Please ask me:

1. **What is the name of the system?**
2. **Who are the direct users of the system?** (human actors)
3. **What external systems does it communicate with?** (other services, APIs, databases outside our boundary)
4. **What data flows INTO the system from outside?**
5. **What data flows OUT OF the system to the outside?**
6. **What communication protocols are used?** (REST, gRPC, messaging, file transfer, etc.)

## Output format

Generate Markdown content ready to replace the placeholder in Chapter 3.

Structure:
- 3.1 Business Context: A brief description + a **PlantUML context diagram** + a table of external actors/systems (System/Actor | Description | Direction)
- 3.2 Technical Context: A table of external interfaces (External System | Communication Protocol | Data Exchanged)

Use a `plantuml` fenced code block for the diagram. See `docs/arc42/pitstop-example.md` Chapter 3 for a reference example using `actor`, `rectangle`, and arrows.

## Tips

- Show ONLY the system boundary — no internal components yet.
- This is NOT the place for internal architecture. Save that for Chapter 5.
- A PlantUML diagram is worth more than paragraphs of text.
- "Direction" means: does data flow in, out, or both ways?
- Include both human users and machine-to-machine integrations.
