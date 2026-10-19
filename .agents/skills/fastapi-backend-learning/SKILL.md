---
name: fastapi-backend-learning
description: Use when this learner designs, implements, tests, or explains FastAPI endpoints, request and response models, dependencies, validation, access checks, database integration, or synchronous and asynchronous request execution.
---

# FastAPI backend learning

Read root AGENTS.md and current learning evidence. Combine with backend-mentor for lessons. Inspect the installed FastAPI, Python, Pydantic, database driver, and test dependencies before version-sensitive examples. Follow the root Context7 documentation workflow; do not silently mix APIs from different major versions.

## Start with one HTTP contract

Describe the caller's operation, method, path, parameters, request body, success response, and relevant failure responses before writing decorators. Trace one request through validation, identity, permission, domain logic, persistence, and public output. Introduce only the part needed for the current milestone.

Keep domain rules understandable outside the framework. Use separate public input/output contracts when their fields or trust differ. Distinguish:

- Python annotations: expectations for code and tooling.
- Pydantic/FastAPI validation: actual parsing and checks at configured boundaries, possibly including coercion.
- Domain rules: what the operation is allowed to do.
- Database constraints: which invalid stored states must be rejected under competing writes.

Make accepted and rejected values explicit; do not assume validation is strict unless configured and checked. Response filtering helps limit fields but does not establish authorization. Avoid returning unrestricted persistence objects or secret fields.

## Dependencies and state

Introduce dependencies for concrete request concerns such as verified identity or a database session. Explain creation, ownership, cleanup, transaction boundaries, and how tests replace dependencies. Keep commit ownership explicit; do not hide it across unrelated layers.

Use temporary memory storage only as labeled local scaffolding. Explain restart and multiple-process behavior before replacing it with PostgreSQL. Add routers or service boundaries when the current size warrants them; avoid a generic repository framework around the first endpoints.

## Identity and resource access

A body or path user ID is a claim, not authenticated identity. Derive the actor from verified credentials. If an actor may operate for another member, define and check that permission explicitly. Enforce team and object access on reads and writes; test another user's and another team's identifiers.

Teach authentication mechanisms from current official guidance when that milestone begins. Do not invent password cryptography or treat a decoded token as a verified one. Explain CORS as a browser access mechanism, separate from server authorization and native mobile clients.

## Execution and verification

Start with a synchronous route and synchronous database path. FastAPI runs normal def path operations and dependencies in a thread pool; calling a normal helper directly does not automatically offload it. In an async handler, blocking I/O still blocks its execution thread. Choose async only with a compatible I/O path and explain waiting, cleanup, cancellation, and CPU-work limits.

For each feature, test meaningful HTTP behavior: successful operation, invalid input, missing resource, domain conflict, and access denial when identity is introduced. Assert status, public fields, and stored effects or absence of effects. Use PostgreSQL for database-specific guarantees. Separate request tests from domain tests, and test race conditions with overlapping connections.

Finish by explaining a changed request or failure and recording only demonstrated learner evidence. Use the official FastAPI tutorial, response-model guide, and concurrency guide for the current implementation details.
