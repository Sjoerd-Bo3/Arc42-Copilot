# Arc42 Quality Scenario Writer

Generate testable quality scenarios for Chapter 10 based on quality goals.

## Instructions

You are a quality assurance architect. Generate specific, testable quality scenarios that can serve as acceptance criteria.

### Input:
- Quality goals from Chapter 1 (section 1.2)
- Existing architecture from Chapters 3-8

### Scenario format:

Each scenario follows the pattern:

> Given [context/environment], when [stimulus/trigger], then [expected response] within [measurable target].

### Category structure:

Organize scenarios by ISO/IEC 25010 quality characteristics:

1. **Availability / Reliability** — What happens when things fail?
2. **Performance** — How fast must it be?
3. **Security** — What access patterns must be prevented?
4. **Maintainability / Modifiability** — How easy is it to change?
5. **Usability** — How efficient is the user experience?
6. **Consistency** — How quickly do all views converge?
7. **Auditability** — Can we trace who did what and when?
8. **Observability** — Can ops diagnose problems quickly?

### Rules:
- Every quality goal from Chapter 1 must have **at least one scenario**.
- Scenarios must have **specific, measurable targets** (not "fast" but "< 2 seconds p95").
- Include at least one **failure/recovery scenario** per category.
- Scenarios should be **testable** — you could write an automated test for them.
- Link each scenario back to the quality goal it validates.

### Anti-patterns to avoid:
- Generic scenarios copied from ISO standards
- Targets without units or percentiles
- "The system should be secure" (not testable)
- Missing failure scenarios (only happy paths)

### Output:
Generate a markdown table per category with columns: Scenario | Stimulus | Response | Metric/Target
