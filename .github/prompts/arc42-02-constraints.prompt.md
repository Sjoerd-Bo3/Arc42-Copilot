---
mode: 'ask'
description: 'Generate arc42 Chapter 2: Architecture Constraints'
---

# Generate arc42 Chapter 2: Architecture Constraints

I am working on arc42 architecture documentation.
Please help me write **Chapter 2: Architecture Constraints** for `docs/arc42/arc42-template.md`.

## Context questions

Please ask me:

1. **What technology stack is mandated?** (e.g. required languages, frameworks, cloud providers)
2. **Are there organizational constraints?** (e.g. team size, budget, vendor relationships, outsourcing)
3. **Are there regulatory or compliance requirements?** (e.g. GDPR, HIPAA, industry standards)
4. **Are there integration mandates?** (e.g. must use company SSO, must connect to existing ERP)
5. **Are there deployment constraints?** (e.g. on-premises only, specific OS, air-gapped network)

## Output format

Generate Markdown content ready to replace the placeholder in Chapter 2.

Structure as three subsections:
- 2.1 Technical Constraints (table: Constraint | Reason / Background)
- 2.2 Organizational Constraints (table: Constraint | Reason / Background)
- 2.3 Conventions and Standards (table: Constraint | Reason / Background)

## Tips

- Only list **real constraints** — things that genuinely limit design choices.
- Each constraint must have a clear reason why it exists.
- Preferences and recommendations do NOT belong here.
- Constraints from this chapter should visibly shape later chapters (strategy, decisions).
