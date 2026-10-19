# Backend learning progress

This file records demonstrated learning and the next useful step. Update it as evidence accumulates.

## Confirmed starting context

- Senior frontend experience with Expo, React, and TypeScript.
- Strong programming, architecture, and management background.
- Python, FastAPI, and SQL proficiency have **not yet been assessed**.
- Confirmed learning pace: **6–10 hours per week**.
- Confirmed local Python: **3.14.6**; use Python 3.14 documentation while that remains the local version.
- Setup or tool availability is preparation, not evidence of learning mastery.

## Current position

- Roadmap: [Backend learning roadmap](ROADMAP.md).
- Capstone: a team equipment checkout service, with PostgreSQL as the first learning database.
- Current milestone: **M1, not started**.
- Next action: complete [Exercise 01: Python domain rules](../exercises/01-python-domain-rules/README.md).
- Start with domain behavior and tests, then explain the request lifecycle and trust boundaries.
- Suggested rhythm: four 90-minute sessions, plus an optional 2–4 hours; adjust based on evidence and energy.

## Milestone status

| Milestone | Status | Evidence needed to complete |
| --- | --- | --- |
| M1 — Python domain rules and request lifecycle | Not started | Domain tests pass; explain hints, validation, trust boundaries, and memory limits. |
| M2 — Synchronous FastAPI slice | Not started | Client demonstration and request-level tests; explain contracts and error responses. |
| M3 — PostgreSQL and relational SQL | Not started | Reproducible schema, useful SQL queries, rejected invalid rows, and an explained query plan. |
| M4 — Durable persistence and migrations | Not started | Restart persistence, isolated PostgreSQL integration tests, migrations, and transaction rollback evidence. |
| M5 — Transactions, concurrency, and retries | Not started | Concurrent checkout, injected failure, and repeated-request behavior verified. |
| M6 — Authentication and authorization | Not started | Identity, roles, and cross-team access tests pass; exposure controls reviewed. |
| M7 — I/O boundaries and failure behavior | Not started | Explain blocking and async behavior; verify slow/unavailable database handling. |
| M8 — Deployment and recovery | Not started | Clean deployment, smoke test, failure investigation, and verified database restoration. |

## Evidence log

| Date | Observation | What it demonstrates | Next step |
| --- | --- | --- | --- |
| 2026-10-19 | Learning plan and pace recorded; no exercise work assessed yet. | No learning evidence yet. | Complete Exercise 01 and review its behavior, tests, and explanation. |

Add concise entries for demonstrated behavior, explanations, and meaningful failures or corrections.
Reference the relevant files or commands when available; record uncertainty rather than inferring mastery.

## Open questions

- What Python habits and concepts are already comfortable in practice?
- What SQL and relational modeling experience can be demonstrated?
- Which HTTP, deployment, and security concepts need explanation versus a quick check?
- What does Exercise 01 reveal about the most useful next difficulty level?

Resolve these through the first exercises where possible; do not block starting on a complete self-assessment.
