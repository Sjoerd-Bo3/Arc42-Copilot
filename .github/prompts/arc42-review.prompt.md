---
mode: 'ask'
description: 'Review the arc42 documentation for completeness, consistency, and quality'
---

# Review arc42 Architecture Documentation

Please review the arc42 architecture documentation in `docs/arc42/arc42-template.md` and provide feedback.

## What to look for

1. **Completeness:** Are all 12 chapters present? Are there placeholder sections that should be filled in?
2. **Consistency:** Do the chapters align with each other?
   - Do the building blocks in Ch5 match what is described in Ch3 (context)?
   - Do quality goals in Ch10 refine the goals stated in Ch1?
   - Do architectural decisions in Ch9 connect to the strategy in Ch4?
   - Are component names used consistently across all chapters?
3. **Quality of content:**
   - Are quality goals measurable (not just buzzwords)?
   - Do architectural decisions include rationale and alternatives considered?
   - Are constraints properly reasoned (with background explanation)?
   - Is the deployment view current and realistic?
4. **Missing elements:**
   - Are there obvious risks or debts that aren't documented?
   - Are there important cross-cutting concerns not covered in Ch8?
   - Is the glossary missing important domain terms?

## Output format

Provide a review report with:
- A summary of what is well-documented
- A prioritized list of gaps or improvements (High / Medium / Low priority)
- Specific suggestions for each identified gap

Please reference specific chapter numbers and sections in your feedback.
