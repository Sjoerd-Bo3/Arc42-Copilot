# arc42 Architecture Documentation

> **Based on the arc42 template** — a pragmatic and proven approach to software architecture documentation.
> Inspired by Michaël Hompus's [Arc42 Practical Series](https://blog.hompus.nl/2026/02/01/arc42-practical-series/).

---

## How to use this template

Fill in each chapter iteratively. Start with what you know, skip what is not relevant yet, and refine over time. The goal is to document *what matters*, not to fill in every blank.

**Tips for getting started:**
- Start with Chapter 1 (Introduction and Goals) — if you only write one chapter, make it this one.
- Use the Copilot prompts in `.github/prompts/` to get AI-generated drafts for each chapter.
- Update this document alongside significant code and architecture changes.
- Keep it close to the code: store this in your repository so it evolves with the system.

---

## Table of Contents

1. [Introduction and Goals](#1-introduction-and-goals)
2. [Architecture Constraints](#2-architecture-constraints)
3. [System Scope and Context](#3-system-scope-and-context)
4. [Solution Strategy](#4-solution-strategy)
5. [Building Block View](#5-building-block-view)
6. [Runtime View](#6-runtime-view)
7. [Deployment View](#7-deployment-view)
8. [Cross-Cutting Concepts](#8-cross-cutting-concepts)
9. [Architectural Decisions](#9-architectural-decisions)
10. [Quality Requirements](#10-quality-requirements)
11. [Technical Risks and Debts](#11-technical-risks-and-debts)
12. [Glossary](#12-glossary)

---

## 1. Introduction and Goals

> **Purpose:** Answer "why are we building this?" and "for whom?" before diving into technical architecture.
> If stakeholders read only one chapter, this is it.

> **Best practices:**
> - Keep it short (1–3 paragraphs max for the problem description).
> - Focus on the top requirements only — not a full requirements catalog.
> - Make quality goals measurable, not just buzzwords.
> - This chapter is the most-read section; avoid jargon.
>
> **Done when:**
> - Someone unfamiliar with the project can understand what it does and why it exists.
> - The top 3–5 quality goals are specific and measurable.
> - Key stakeholders and their expectations are listed.

_[1–3 short paragraphs: what are we building, why now, what pain does it solve?]_

### 1.1 Requirements Overview

**The most important requirements:**

- _[requirement 1]_
- _[requirement 2]_
- _[requirement 3]_

**Explicit non-goals:**

- _[what this system intentionally does NOT do]_

### 1.2 Quality Goals

| Priority | Quality Goal    | Scenario                                      | Acceptance Criteria                          |
| -------: | :-------------- | :-------------------------------------------- | :------------------------------------------- |
| 1        | _[e.g. Availability]_ | _[e.g. Workshop mode with intermittent connectivity]_ | _[e.g. System remains functional for 30+ minutes offline]_ |
| 2        | _[quality goal]_ | _[scenario]_                                 | _[measurable criterion]_                     |
| 3        | _[quality goal]_ | _[scenario]_                                 | _[measurable criterion]_                     |

### 1.3 Stakeholders

| Stakeholder              | Role / Interest                             | Key Expectations                             |
| :----------------------- | :------------------------------------------ | :------------------------------------------- |
| _[e.g. Product Owner]_   | _[defines priorities and requirements]_     | _[system meets business goals]_              |
| _[e.g. Development Team]_ | _[builds and maintains the system]_        | _[clear architecture and interfaces]_        |
| _[e.g. End User]_         | _[uses the system daily]_                  | _[fast, reliable, easy to use]_              |

---

## 2. Architecture Constraints

> **Purpose:** List everything that restricts your design or implementation choices.
> Constraints come before solutions — they are non-negotiable limits, not preferences.

> **Best practices:**
> - Only list real constraints, not preferences or guidelines.
> - Categorize: technical, organizational, regulatory/legal.
> - Explain the *reason* behind each constraint — helps future architects understand context.
>
> **Done when:**
> - Any developer or architect can identify boundaries they must respect.
> - The list is focused on genuine restrictions, not a wishlist.

### 2.1 Technical Constraints

| Constraint                | Reason / Background                          |
| :------------------------ | :------------------------------------------- |
| _[e.g. Must run on .NET 8 LTS]_ | _[company-wide standard, support lifecycle aligns with Microsoft LTS policy]_ |
| _[technology constraint]_  | _[reason]_                                  |

### 2.2 Organizational Constraints

| Constraint                | Reason / Background                          |
| :------------------------ | :------------------------------------------- |
| _[e.g. 2-person team]_    | _[budget limitations]_                       |
| _[organizational constraint]_ | _[reason]_                             |

### 2.3 Conventions and Standards

| Constraint                | Reason / Background                          |
| :------------------------ | :------------------------------------------- |
| _[e.g. OpenAPI for all REST endpoints]_ | _[company API governance policy]_ |
| _[convention]_            | _[reason]_                                   |

---

## 3. System Scope and Context

> **Purpose:** Define what is inside and outside your system — external systems, actors, and interfaces.
> This chapter answers: "what does the system interact with?"

> **Best practices:**
> - Use a context diagram (even a simple box diagram) to make boundaries visual.
> - Include external systems, users, and third-party services.
> - Do NOT describe internals here — keep it to the system boundary.
> - Use the technical context to document communication protocols.
>
> **Done when:**
> - You can draw a clear boundary between your system and the outside world.
> - All significant external systems and actors are identified.

### 3.1 Business Context

_[Describe the system in its business environment. Who uses it? What data flows in and out?]_

```
[Context Diagram — replace with actual diagram tool (Mermaid, PlantUML, C4, etc.)]

┌──────────────────────────────────────────────────────────────┐
│                                                              │
│                     [Your System Name]                       │
│                                                              │
└──────────────────────────────────────────────────────────────┘
        ↑                      ↑                    ↑
  [External Actor 1]   [External System A]   [External System B]
```

| External System / Actor  | Description                                  | Direction          |
| :----------------------- | :------------------------------------------- | :----------------- |
| _[Actor/System Name]_    | _[what it is, why it interacts]_             | _[in / out / both]_ |

### 3.2 Technical Context

| External System / Interface | Communication Protocol       | Data Exchanged               |
| :--------------------------- | :--------------------------- | :--------------------------- |
| _[System/Service Name]_      | _[e.g. REST/HTTPS, gRPC]_   | _[e.g. JSON events, CSV files]_ |

---

## 4. Solution Strategy

> **Purpose:** Summarize the fundamental architecture decisions and design approaches that shape the system.
> This is your "big picture" — the strategic direction before the details.

> **Best practices:**
> - Focus on the *why* behind decisions, not just what was decided.
> - Keep this a living list: add entries as the system evolves.
> - Link to specific ADRs (Chapter 9) for decisions that need detailed explanation.
> - Cover: technology choices, top-level decomposition strategy, integration approach.
>
> **Done when:**
> - A new team member understands the architectural direction after reading this chapter.
> - Each strategy maps back to a quality goal or constraint.

| Strategy                 | Decision / Approach                          | Rationale                                    |
| :----------------------- | :------------------------------------------- | :------------------------------------------- |
| _[e.g. Deployment model]_ | _[e.g. Containerized microservices on Kubernetes]_ | _[scalability goal, team expertise]_   |
| _[e.g. Data storage]_    | _[e.g. PostgreSQL for transactional data, Redis for cache]_ | _[reliability + performance goals]_ |
| _[e.g. API design]_      | _[e.g. REST with OpenAPI contracts]_         | _[organizational API standard, tooling ecosystem]_ |
| _[strategy area]_         | _[decision]_                                | _[rationale, links to ADR if applicable]_    |

---

## 5. Building Block View

> **Purpose:** Show the static structure of the system — main components, their responsibilities, and dependencies.
> This is the "map" of your software.

> **Best practices:**
> - Use hierarchical decomposition: start coarse, go deeper only where needed.
> - Describe responsibilities and interfaces, NOT implementation details.
> - Avoid describing behavior here — that belongs in Chapter 6 (Runtime View).
> - Align components with team boundaries where possible (Conway's Law in action).
>
> **Done when:**
> - The top-level breakdown is clear and matches the actual code structure.
> - Each component has a clear owner and responsibility.

### 5.1 Level 1 — Top-Level Decomposition

_[High-level overview of the system. Show the main building blocks and their relationships.]_

```
[Building Block Diagram — Level 1]

┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│   [Component A] │────▶│   [Component B] │────▶│   [Component C] │
└─────────────────┘     └─────────────────┘     └─────────────────┘
```

| Building Block        | Responsibility                               | Key Interfaces / Dependencies                |
| :-------------------- | :------------------------------------------- | :------------------------------------------- |
| _[Component A]_       | _[what it does in one sentence]_             | _[REST API → Component B, DB connection]_    |
| _[Component B]_       | _[what it does in one sentence]_             | _[consumes events from A, publishes to C]_   |

### 5.2 Level 2 — Internal Decomposition of _[Component Name]_

> _[Repeat this section for components that benefit from a deeper breakdown]_

_[Describe sub-components of the component above]_

---

## 6. Runtime View

> **Purpose:** Describe important dynamic behaviors — how components interact at runtime to achieve key use cases or handle failures.

> **Best practices:**
> - Select 2–5 *critical* scenarios: the happy path, a significant error case, a key integration.
> - Use sequence diagrams or numbered steps — whatever is clearest.
> - Do NOT repeat the static structure from Chapter 5 here.
> - Focus on the "what happens" and "in what order".
>
> **Done when:**
> - The key user flows and error paths are documented.
> - Someone can trace a request end-to-end through the system.

### Scenario 1: _[Scenario Name — e.g. User Login]_

_[Brief description of what happens]_

```
[Sequence Diagram or Step-by-Step Description]

User → [Component A]: request
[Component A] → [Component B]: validate
[Component B] → [Component A]: result
[Component A] → User: response
```

### Scenario 2: _[Scenario Name — e.g. Error Handling / Failure Case]_

_[Brief description of what happens when something goes wrong]_

---

## 7. Deployment View

> **Purpose:** Show where and how the software runs — infrastructure, environments, and the mapping of components to deployment targets.

> **Best practices:**
> - Include a deployment diagram showing nodes, containers, and their connections.
> - Cover *all relevant environments*: production, staging, dev if they differ significantly.
> - Keep in sync with the actual deployment — stale deployment docs are worse than none.
> - Document deployment constraints that influence architecture decisions.
>
> **Done when:**
> - It is clear where each component runs and how they communicate over the network.
> - Environment differences (prod vs. staging) are documented.

### 7.1 Infrastructure Overview

```
[Deployment Diagram]

Cloud Provider / On-Premises
├── [Environment: Production]
│   ├── [Node/Cluster: e.g. Kubernetes Cluster]
│   │   ├── [Pod: Component A]
│   │   └── [Pod: Component B]
│   └── [Managed Service: e.g. Azure SQL Database]
└── [Environment: Staging]
    └── [...]
```

### 7.2 Environment Mapping

| Environment    | Purpose                    | Notable Differences from Production          |
| :------------- | :------------------------- | :------------------------------------------- |
| Production     | Live user traffic          | Full scale, real data                        |
| Staging        | Pre-release validation     | _[e.g. Reduced scale, anonymized data]_      |
| Development    | Developer testing          | _[e.g. Local, mocked external services]_     |

---

## 8. Cross-Cutting Concepts

> **Purpose:** Document overarching principles and patterns that apply across multiple components — the "rules" the whole system follows.

> **Best practices:**
> - Include concepts that affect at least 2+ components.
> - Document the *why* — what problem does the concept solve?
> - Reference this chapter from other chapters to avoid repetition.
> - Common topics: security, error handling, logging, observability, data validation, API versioning.
>
> **Done when:**
> - New team members can understand the "house rules" by reading this chapter.
> - Each concept explains both the pattern and its rationale.

### 8.1 Security

_[Authentication/authorization approach, secrets management, network security]_

### 8.2 Error Handling and Resilience

_[How errors are caught, logged, and surfaced. Retry strategies, circuit breakers, fallbacks]_

### 8.3 Logging and Observability

_[Logging format, log levels, tracing approach, metrics collection, alerting strategy]_

### 8.4 API Design

_[REST vs gRPC vs messaging. Versioning strategy. Contract testing approach]_

### 8.5 Data Validation

_[Where and how data is validated. Input sanitization approach]_

### 8.6 Configuration Management

_[How configuration is managed across environments. Secrets handling]_

---

## 9. Architectural Decisions

> **Purpose:** Create a timeline of significant decisions so future developers understand *why* the system is built the way it is.
> Architecture Decision Records (ADRs) go here.

> **Best practices:**
> - Record decisions that have significant, lasting impact.
> - For each decision: what was decided, why, and what alternatives were considered.
> - Skip easily reversible or trivial decisions.
> - This chapter should grow over time — that's healthy!
> - Use a table for a quick overview; link to separate ADR files for complex decisions.
>
> **Done when:**
> - Key irreversible or costly decisions are documented.
> - The rationale can be understood without needing to interview the original authors.

| Date       | Decision                             | Status       | Rationale / Alternatives Considered          |
| :--------- | :----------------------------------- | :----------- | :------------------------------------------- |
| YYYY-MM-DD | _[e.g. Use event-driven architecture]_ | Accepted   | _[scalability needs; considered REST polling, rejected due to latency]_ |
| YYYY-MM-DD | _[decision title]_                   | _[status]_   | _[rationale, link to ADR file if detailed]_  |

> **ADR Status values:** Proposed | Accepted | Deprecated | Superseded by [ADR-xxx]

---

## 10. Quality Requirements

> **Purpose:** Translate the high-level quality goals from Chapter 1 into concrete, testable scenarios.

> **Best practices:**
> - Refine quality goals into specific, measurable scenarios.
> - Use quality trees to organize: Quality Goal → Scenario → Acceptance Criterion.
> - Reference ISO/IEC 25010 categories if helpful (performance, reliability, usability, etc.).
> - Update this as the system evolves — quality requirements can change.
>
> **Done when:**
> - Each quality goal has at least one concrete, testable scenario.
> - Acceptance criteria are specific enough to be tested or verified.

### Quality Tree

```
Quality Goals
├── [Quality Goal 1: e.g. Availability]
│   ├── Scenario: [describe the situation]
│   └── Acceptance: [measurable criterion]
├── [Quality Goal 2: e.g. Performance]
│   ├── Scenario: [describe the situation]
│   └── Acceptance: [measurable criterion]
└── [Quality Goal 3: e.g. Maintainability]
    ├── Scenario: [describe the situation]
    └── Acceptance: [measurable criterion]
```

### Quality Scenarios

| Quality Goal  | Stimulus                             | System Response                      | Acceptance Criterion                         |
| :------------ | :----------------------------------- | :----------------------------------- | :------------------------------------------- |
| _[Availability]_ | _[Primary database goes offline]_ | _[System switches to read-only replica]_ | _[Within 5 seconds, zero data loss]_     |
| _[Performance]_  | _[100 concurrent users log in]_   | _[System handles all requests]_      | _[P95 response time < 500ms]_                |
| _[goal]_         | _[stimulus]_                      | _[response]_                         | _[measurable criterion]_                     |

---

## 11. Technical Risks and Debts

> **Purpose:** Make risks and technical debt visible and actionable — not to complain, but to prioritize and plan.

> **Best practices:**
> - Be honest: hidden risks are worse than documented ones.
> - For each item: what is the risk, what is the potential impact, and what is the mitigation?
> - Include technical debt that may affect future architecture decisions.
> - Review and update regularly — especially before major releases or refactoring phases.
>
> **Done when:**
> - Known risks are visible to the whole team.
> - Each risk has a clear owner and at least a mitigation idea.

### 11.1 Known Risks

| Risk                     | Probability | Impact  | Mitigation Strategy                          |
| :----------------------- | :---------- | :------ | :------------------------------------------- |
| _[e.g. Single point of failure in message broker]_ | Medium | High | _[Add redundancy, implement circuit breaker]_ |
| _[risk description]_     | _[Low/Medium/High]_ | _[Low/Medium/High]_ | _[mitigation or acceptance]_ |

### 11.2 Technical Debt

| Area                     | Description                                  | Consequence if Ignored                       | Priority     |
| :----------------------- | :------------------------------------------- | :------------------------------------------- | :----------- |
| _[e.g. Authentication module]_ | _[Uses deprecated library, no MFA support]_ | _[Security vulnerability when library loses support]_ | High |
| _[area]_                 | _[description]_                             | _[consequence]_                              | _[priority]_ |

---

## 12. Glossary

> **Purpose:** Define key terms and domain concepts to ensure a shared vocabulary across the team.

> **Best practices:**
> - Include terms that cause confusion or have special project-specific meaning.
> - Keep it focused — not every technical term needs an entry.
> - Update regularly; prune obsolete terms.
> - Include both domain terms and important technical abbreviations.
>
> **Done when:**
> - New team members can look up unfamiliar project-specific terms here.
> - Domain experts and developers share the same vocabulary.

| Term                     | Definition                                                   |
| :----------------------- | :----------------------------------------------------------- |
| _[Term]_                 | _[Clear, concise definition in the context of this system]_  |
| _[Abbreviation]_         | _[What it stands for and what it means here]_                |

---

## Keeping This Documentation Alive

> Architecture documentation is only valuable when it reflects reality. Here are practices to keep it alive:

- **Update with every significant change:** Treat architecture docs like code — update them when the design changes.
- **Own it as a team:** Documentation is not just the architect's job. Everyone who changes the architecture updates the docs.
- **Review in retrospectives:** Periodically check if the documentation still reflects the current state.
- **Use Architecture Decision Records (ADRs):** Record key decisions in Chapter 9 with the date and rationale.
- **Link from code:** Reference relevant architecture sections in pull request descriptions and code comments where applicable.
- **Keep it in the repository:** Documentation lives next to the code so it is versioned, reviewed, and visible.

---

*Template inspired by [arc42](https://arc42.org/) and the [Arc42 Practical Series by Michaël Hompus](https://blog.hompus.nl/2026/02/01/arc42-practical-series/).*
