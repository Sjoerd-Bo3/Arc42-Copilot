---
mode: 'ask'
description: 'Generate arc42 Chapter 11: Technical Risks and Debts'
---

# Generate arc42 Chapter 11: Technical Risks and Debts

I am working on arc42 architecture documentation.
Please help me write **Chapter 11: Technical Risks and Debts** for `docs/arc42/arc42-template.md`.

## Context questions

Please ask me:

1. **What are the known technical risks?** (things that could go wrong and impact quality or delivery)
2. **For each risk: what is the probability?** (Low / Medium / High)
3. **For each risk: what is the potential impact?** (Low / Medium / High)
4. **For each risk: is there a mitigation in place or planned?**
5. **What technical debt exists?** (shortcuts taken, aging components, known architectural weaknesses)
6. **For each debt item: what happens if it is not addressed?** (consequence)
7. **For each debt item: what is the priority?** (Low / Medium / High)

## Output format

Generate Markdown content ready to replace the placeholder in Chapter 11.

Structure:
- 11.1 Known Risks table: Risk | Probability | Impact | Mitigation Strategy
- 11.2 Technical Debt table: Area | Description | Consequence if Ignored | Priority

## Tips

- Be honest: undocumented risks are more dangerous than acknowledged ones.
- Each risk needs an owner, even if it's "the team".
- Technical debt includes: outdated dependencies, missing tests, hard-coded configurations, monolithic modules that need splitting.
- Distinguish between risks (things that *might* happen) and debt (things that are *already* a problem).
- Revisit this chapter before major releases or significant refactoring efforts.
- If a risk is accepted (won't be mitigated), say so explicitly with the reason.
