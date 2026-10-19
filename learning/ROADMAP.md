# Backend learning roadmap

Build backend judgment by extending one small service, with working evidence at every step.
Your existing programming, architecture, and delivery experience lets us focus on unfamiliar backend concepts.

## Pace and working rhythm

- Confirmed pace: **6–10 hours per week**.
- Suggested rhythm: four 90-minute sessions, plus an optional 2–4 hours for practice or consolidation.
- Each exchange targets one concept or coherent pair: read/predict, run, explain, modify, or build as useful. Give feedback before adding the next chunk.
- Milestones are readiness checks, not weekly deadlines. Repeat or split a milestone when evidence warrants it.
- [PROGRESS.md](PROGRESS.md) shows the current step; [HISTORY.md](HISTORY.md) preserves attempts and quiz feedback; [CONCEPTS.md](CONCEPTS.md) holds evidence and the review queue.
- Use [TEACHING.md](TEACHING.md) to adapt examples, support, order, and review. Preserve prerequisite/outcome goals and explain changes rather than silently replace the plan.
- Syntax lookup is allowed. Practice concept retrieval and code reading; check transfer with changed requirements and later retrieval.

## One capstone: team equipment checkout

Members browse equipment, check out an available item, and return it. Managers maintain inventory.
Start with one team; add a second team when testing access boundaries.
The eventual model includes users, teams, memberships, equipment, and loans.
The central invariant is that equipment has at most one active loan.
Keep the system to one application and one PostgreSQL database while learning the essentials.

## M1 — Python domain rules and the request lifecycle

**Build:** Complete [Exercise 01: Python domain rules](../exercises/01-python-domain-rules/README.md).
Start with the dashboard's small diagnostic; the interrupted/discarded lesson is not completed instruction or assessment.
Start with checkout; after the first exercise, extend to return and availability behavior with focused tests.
Practice modules, collections, mutability, exceptions, type hints, and a reproducible project environment.

**Explain:** Trace a request from client to server, domain logic, database, and response.
Place DNS and TLS on that path, and distinguish HTTP methods, headers, bodies, and status codes.
Mark where untrusted input enters and where validation, identity, permissions, and persistence belong.
Explain the difference between type hints and runtime validation, and between process memory and durable data.

**Verify:** Tests cover successful checkout, duplicate checkout, return, and unknown equipment.
Trace a small function, explain mutation/error paths, and revisit a changed case after a delay.
Explain why the in-memory model cannot guarantee correctness across processes or concurrent requests.
Fold this foundation work into the first learning sessions; do not repeat basic programming material.

## M2 — A small synchronous FastAPI slice

**Build:** Add a small HTTP interface around the domain rules using temporary in-memory storage.
Use explicit request and response models, deliberate status codes, and consistent error responses.
Keep the first implementation synchronous so the execution model is easy to trace.

**Explain:** Distinguish HTTP contracts, runtime validation, domain rules, and internal representations.
Describe which response fields clients may see and why response validation matters.

**Verify:** Request-level tests cover valid input, invalid input, missing equipment, and unavailable equipment.
Read an endpoint/dependency path and locate identity, rules, state changes, and public output.
Demonstrate the API from a client and explain each response. Keep this exercise local.
Before any service is exposed, apply the security controls appropriate to its access and data.

## M3 — PostgreSQL and relational SQL before an ORM

**Build:** Use PostgreSQL as the first learning database and write SQL directly.
Model equipment and loan history, then extend the schema with teams and memberships.
Practice joins, aggregates, foreign keys, nullability, uniqueness, indexes, and basic query plans.

**Explain:** Describe cardinality, ownership, keys, and which invariants belong in database constraints.
Explain why checking a rule in application code does not make concurrent writes safe.

**Verify:** Recreate a database from your schema and sample data; query availability and loan history.
Predict query results and explain which constraint protects which invariant before running them.
Show constraints rejecting invalid rows and explain an index using a representative query plan.
Explore SQLite differences later, after PostgreSQL behavior is understood; do not assume interchangeability.

## M4 — Durable request-to-database integration

**Build:** Replace process memory with PostgreSQL, keeping the existing HTTP contract useful.
Now introduce SQLAlchemy and Alembic for persistence and migrations, while inspecting the resulting SQL.
Use a synchronous database path initially; make connection, session, and transaction lifetimes explicit.

**Explain:** Trace one request through persistence and identify commit, rollback, and resource cleanup.
Distinguish application objects, database rows, API models, and schema migrations.

**Verify:** Data survives restarts; integration tests use PostgreSQL and isolate their data.
Trace a write through SQL, commit, failure, and cleanup; diagnose a changed failure case.
A fresh database reaches the current schema through migrations, and a failed operation leaves no partial change.
Explain the SQL behind representative ORM reads and writes before adding abstraction.

## M5 — Transactions, concurrency, and retries

**Build:** Enforce at most one active loan per equipment item in PostgreSQL.
Choose transaction behavior and conflict responses; define how repeated checkout requests behave.

**Explain:** Walk through two simultaneous checkouts and identify the database's deciding operation.
Distinguish a transaction, isolation, locking, an invariant, and request idempotency.
Explain which failures are safe to retry, and why retries need bounds and a clear contract.

**Verify:** Concurrent checkout attempts result in exactly one active loan and a deliberate loser response.
Predict an interleaving before an optional timeline activity; explain the deciding database operation.
Inject a failure to demonstrate rollback. Repeat a request and prove it cannot create duplicate effects.
Keep these tests as regression evidence when the persistence code changes.

## M6 — Authentication and authorization

**Build:** Establish identity using a standard authentication mechanism and enforce team and role permissions.
Treat client-supplied identifiers as untrusted; check access to each requested resource.
Add appropriate secret handling, transport protection, and abuse controls before exposing the service.

**Explain:** Distinguish authentication from authorization and server enforcement from client presentation.
Describe credential handling, permission checks, and which response fields must remain private.

**Verify:** Tests cover anonymous users, members, managers, and members of another team.
Read an access check and construct a request exposing a missing permission boundary.
Changing an equipment ID cannot bypass access checks; unauthorized writes cause no database changes.
Review exposed routes and failure responses for accidental data or secret disclosure.

## M7 — I/O boundaries, async, and failure behavior

**Build:** Add timeouts and useful failure reporting; examine the working synchronous implementation first.
Only then experiment with an asynchronous I/O path where its driver and workload justify it.
Introduce background work only when a concrete requirement needs it.

**Explain:** Identify blocking calls and distinguish concurrency from CPU parallelism.
Describe what changes at an async boundary, including resource lifetime and cancellation.
Distinguish latency from throughput when comparing workloads and results.

**Verify:** Demonstrate predictable responses when the database is unavailable or slow.
Trace blocking/waiting; use an interactive timeline only if it clarifies the distinction.
Compare representative concurrent requests before and after any async change; retain correctness tests.
Explain the observed behavior without assuming that async automatically improves performance.

## M8 — Deployment, observation, and recovery

**Build:** Deploy one application and PostgreSQL with configuration, secrets, logs, and health checks.
Define a migration procedure, backup policy, restore procedure, and a recoverable release path.

**Explain:** Trace a failed request using logs and describe application/schema compatibility during release.
Distinguish an application restart, deployment rollback, schema recovery, and database restoration.

**Verify:** Deploy from a clean environment, run a smoke test, and investigate a deliberate failure.
Read configuration, logs, and migration instructions to explain failure and recovery.
Restore sample data into a separate database and verify both its contents and application behavior.
Recheck authentication, authorization, concurrency, and secret handling in the deployed environment.

## Official references

- [Python 3.14 tutorial](https://docs.python.org/3.14/tutorial/) — matches the confirmed local Python 3.14.6 major/minor.
- [Python 3.14 typing](https://docs.python.org/3.14/library/typing.html) — annotations do not enforce runtime types.
- [FastAPI tutorial](https://fastapi.tiangolo.com/tutorial/), [request bodies](https://fastapi.tiangolo.com/tutorial/body/), and [response models](https://fastapi.tiangolo.com/tutorial/response-model/).
- [FastAPI concurrency and async](https://fastapi.tiangolo.com/async/) — revisit after the synchronous path is understood.
- [PostgreSQL tutorial](https://www.postgresql.org/docs/17/tutorial.html) and [constraints](https://www.postgresql.org/docs/17/ddl-constraints.html) — versioned references, not a PostgreSQL version selection.

Use documentation matching the installed version when implementation begins; these links do not prescribe upgrades.
