# 8. Crosscutting Concepts

> **Purpose**: Document patterns and decisions that affect multiple building blocks. These are the "rules of the house" — how things are done consistently across the system.

> **What belongs here**: Authentication, logging, error handling, data access patterns, integration strategies, observability, caching, etc.

## 8.1 Authentication and Authorization

<!-- How are users identified? What authorization model (RBAC, ABAC, claims)? -->

> **Tip**: Include a concrete example of how roles map to permissions. Abstract RBAC descriptions are useless without examples.

## 8.2 Logging and Observability

<!-- Structured logging format, key metrics, alert thresholds. -->

> **Tip**: Define 3-5 key metrics that ops will actually watch. More metrics = more noise.

## 8.3 Error Handling and Resilience

<!-- Global patterns: retry strategy, circuit breaker, dead-letter queues. -->

> **Tip**: Show the actual retry configuration, not just "we use exponential backoff".

## 8.4 Data Persistence

<!-- Database strategy, migration approach, caching. -->

## 8.5 Integration Patterns

<!-- How does the system talk to external systems? Include example payloads. -->

> **Anti-pattern**: Documenting crosscutting concepts as abstract principles without concrete implementation details. "We use structured logging" means nothing without showing the log format.

> **Anti-pattern**: Putting everything here. This chapter is for patterns that span multiple blocks. A concept used by only one component belongs in that component's documentation.

## Completion Checklist

- [ ] Each concept includes a concrete implementation example
- [ ] Concepts that span multiple blocks are here (not in individual component docs)
- [ ] Security approach includes role/permission mapping
- [ ] Observability includes specific metrics and alert thresholds
- [ ] Integration patterns include retry/failure handling
