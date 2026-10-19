---
name: relational-database-learning
description: Use when this learner studies relational modeling, database tables, SQL, keys, relationships, constraints, transactions, concurrency, indexes, query plans, or schema migrations. PostgreSQL is the default learning database.
---

# Relational database learning

Read root AGENTS.md and current learning evidence. Combine with backend-mentor for lessons. Start from the domain's questions and invariants; teach SQL before an ORM obscures its behavior.

## Design from use cases

For the current feature, identify the facts stored, questions answered, and rules that must always hold. Separate a current state from its history. For checkout, an equipment item and a loan event have different identities and lifetimes.

Produce only the schema detail needed for the lesson:

- Entities and a small relationship sketch with cardinality and optionality.
- Columns with types, primary keys, foreign keys, nullability, meaningful defaults, and reasons.
- Uniqueness and check constraints tied to explicit invariants.
- Deletion behavior: reject, cascade, retain history, or archive, with the domain consequence.
- Representative queries and indexes justified by those queries or integrity needs.

Begin with normalized relationships rather than tables copied from screens or duplicated names in every row. Explain when a join table represents a many-to-many relation. Treat denormalization and JSON storage as choices with demonstrated query and consistency tradeoffs.

## Practice SQL visibly

Give small fixture rows and expected query results. Build from reads and writes to filtering, joins, aggregation, ordering, and pagination. Specify deterministic ordering when a result must be stable. Use parameterized values for untrusted input.

Have the learner demonstrate a constraint rejecting invalid data, not merely describe the happy path. Distinguish application validation from database enforcement. Use official PostgreSQL documentation matching the installed version through the root documentation workflow.

## Transactions and concurrency

Teach atomicity separately from isolation. A transaction around a check followed by an insert does not by itself prevent a competing request from passing the same check.

Trace two actors before choosing a database mechanism. Identify the exact invariant, what operation enforces it, commit/rollback boundaries, and how conflicts surface. Introduce conditional writes, uniqueness, locking, or stronger isolation as the problem requires; explain retry behavior and limits.

For active-loan uniqueness, discuss a constraint/index covering active rows once the learner understands basic constraints. Do not pretend a row-level check constraint can enforce arbitrary cross-row rules.

Verify concurrency with separate PostgreSQL connections and deliberately overlapping operations; inspect the final stored state. Two sequential calls or SQLite tests do not establish concurrent PostgreSQL correctness.

## Performance and evolution

Derive indexes from filters, joins, ordering, and uniqueness. Discuss read benefit, write/storage cost, and actual query plans. Foreign keys do not automatically create indexes on PostgreSQL's referencing columns. Distinguish query count problems from slow individual queries when introducing an ORM.

Teach migrations as versioned changes to both schema and existing data. Check fresh creation and upgrades with representative old rows, including backfills and constraints. Explain release compatibility and recovery rather than assuming every migration can be safely reversed.
