# 1. Introduction and Goals

Most garages use a planning tool for appointments and a separate admin/workshop system for execution. When jobs change (delay, extra work, parts missing), updates are handled manually, causing schedule drift, wrong customer expectations, and inefficient workshop utilization.

**Pitstop solves this by providing a single operational source of truth for work orders and status, and synchronizing planning + workshop execution.**

## 1.1 Requirements Overview

| Requirement | Description | Priority |
|-------------|-------------|----------|
| Import appointments | From one or more Planning Services | High |
| Work Orders | Convert appointments into jobs/tasks with estimates, skills, bay assignment | High |
| Admin Overview | Today's workload, lateness, bay utilization, priorities | High |
| Workshop View | Per bay/technician task list with fast status updates and notes | High |
| Status sync | Push status changes back to planning (delays, ready-for-pickup, reschedule) | High |
| Parts tracking | Track "Waiting for Parts" to block/advance work | Medium |

**Explicit non-goals:**

- Pitstop is **not** the planning product.
- Pitstop is **not** inventory management (it references parts status, doesn't manage stock).
- Pitstop is **not** billing/accounting (it can export outcomes, doesn't own invoicing).

## 1.2 Quality Goals

| Priority | Quality | Scenario (short) | Acceptance criteria |
|---------:|---------|-------------------|---------------------|
| 1 | Consistency | Admin + Workshop must show the same job state | Status updates visible in all UIs within **2 seconds** |
| 2 | Availability | Workshop continues during flaky internet | Workshop View works in **degraded mode**; updates sync when online |
| 3 | Modifiability | Add a new planning integration | New integration in **2 days** without changing core domain logic |
| 4 | Auditability | Resolve disputes and analyze throughput | Every change includes **who/when/why**, immutable history |
| 5 | Usability | Workshop updates must be fast | "Glove-friendly" UX: **3 taps, 5s** max |

## 1.3 Stakeholders

| Stakeholder | Expectations |
|-------------|-------------|
| Garage Owner / Manager | Throughput, predictable planning, fewer no-shows, visibility |
| Service Advisor (front desk) | Reliable customer promises, quick rescheduling |
| Workshop Foreman | Clear priorities, balanced bays, fewer interruptions |
| Mechanics | Simple task list, fast updates, less admin burden |
| Customer | Accurate ETA, proactive updates on delays |
| Planning Vendor(s) | Stable API usage, predictable traffic, clean sync semantics |
| IT/Ops | Deployable, monitorable, secure, low maintenance |
