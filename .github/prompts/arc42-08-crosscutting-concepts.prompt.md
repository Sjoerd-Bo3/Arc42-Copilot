---
mode: 'ask'
description: 'Generate arc42 Chapter 8: Cross-Cutting Concepts'
---

# Generate arc42 Chapter 8: Cross-Cutting Concepts

I am working on arc42 architecture documentation.
Please help me write **Chapter 8: Cross-Cutting Concepts** for `docs/arc42/arc42-template.md`.

## Context questions

Please ask me:

1. **How is authentication and authorization handled?** (e.g. JWT, OAuth2, RBAC, API keys)
2. **How are errors handled and surfaced?** (error formats, retry strategies, circuit breakers)
3. **What is the logging and observability approach?** (log format, log levels, tracing, metrics, alerting)
4. **How is the API designed?** (REST, gRPC, versioning strategy, contract approach)
5. **How is data validated?** (where validation happens, what library/approach)
6. **How is configuration managed?** (environment variables, config files, secrets management)
7. **Are there other cross-cutting concerns?** (e.g. caching, pagination, internationalization, accessibility)

## Output format

Generate Markdown content ready to replace the placeholder in Chapter 8.

Structure: One subsection per cross-cutting concept, covering:
- What the concept is
- The chosen approach
- The rationale (why this approach)
- Any key decisions or constraints

Only include sections relevant to this system — skip sections that are not applicable.

## Tips

- Include only concepts that affect 2+ components — truly "cross-cutting".
- Explain the rationale, not just the mechanics.
- Reference this chapter from other chapters instead of repeating the same information.
- Common cross-cutting concepts: security, error handling, logging, API design, validation, configuration, caching, pagination, data formats, testing approach.
- If a concept has a detailed design decision behind it, link to the relevant ADR in Chapter 9.
