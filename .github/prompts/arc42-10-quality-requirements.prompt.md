---
mode: 'ask'
description: 'Generate arc42 Chapter 10: Quality Requirements'
---

# Generate arc42 Chapter 10: Quality Requirements

I am working on arc42 architecture documentation.
Please help me write **Chapter 10: Quality Requirements** for `docs/arc42/arc42-template.md`.

## Context questions

Please ask me:

1. **What are the quality goals from Chapter 1?** (refer back to the Introduction and Goals)
2. **For each quality goal: what is a realistic failure or stress scenario?** (the stimulus)
3. **For each scenario: what should the system do?** (the expected response)
4. **For each scenario: what is the measurable acceptance criterion?** (specific, testable metric)
5. **Are there quality scenarios that are NOT already covered by the Chapter 1 quality goals?**

## Output format

Generate Markdown content ready to replace the placeholder in Chapter 10.

Structure:
- A Quality Tree showing the hierarchy of quality goals and their scenarios
- A Quality Scenarios table: Quality Goal | Stimulus | System Response | Acceptance Criterion

## Tips

- This chapter refines Chapter 1's quality goals into testable scenarios.
- Each scenario must have a **measurable acceptance criterion** — avoid vague statements.
- Use ISO/IEC 25010 quality categories if helpful: Performance Efficiency, Reliability, Security, Maintainability, Portability, Usability, Compatibility, Functional Suitability.
- Good format: "When [stimulus], the system [response] within [criterion]."
- Example: "When 500 concurrent users submit forms, 95% of requests complete within 300ms with no errors."
- Include both normal-operation scenarios and failure/stress scenarios.
- Quality scenarios can be used as input for performance testing and acceptance testing.
