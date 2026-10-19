---
name: python-backend-learning
description: Use when this learner studies Python language behavior, types, mutability, exceptions, modules, resource management, or Python-specific backend mistakes. Framework and database design questions use their own domain skills.
---

# Python for backend learning

Read root AGENTS.md for learner context and documentation rules. Combine with backend-mentor during lessons. Build on JavaScript/TypeScript knowledge while making Python's actual behavior explicit.

## Choose the smallest language bridge

Teach only the language features the current task needs. Start with functions, dictionaries, sets, lists, iteration, unpacking, None, exceptions, imports, and annotations. Introduce classes, dataclasses, iterators, decorators, and context managers through a concrete use case rather than a syntax tour.

Distinguish these recurring traps with prediction-and-run experiments:

- Annotations describe expectations; Python itself does not enforce them. Static analysis, explicit runtime checks, and framework validation are different mechanisms.
- Mutable default arguments can retain changes across calls. Contrast a fresh per-call collection with deliberately shared state; name its owner and lifetime.
- Assignment, aliasing, shallow copying, and nested mutable values determine which object changes. A shallow copy is not an independent copy of every nested object.
- Truthiness differs from checking for missing values. Compare an explicit None check with valid empty, zero, and false values.
- Boolean values are also instances of int. If a boundary requires integer IDs or counts while excluding booleans, make that rule explicit and test it.
- Exceptions should communicate deliberate failure; broad catching must not turn programming errors into successful results.

Use modern syntax supported by the actual interpreter. Inspect the existing environment before proposing package or interpreter changes. Follow the root Context7 workflow for Python-specific documentation questions and cite the relevant official version.

## Backend habits

Keep business rules callable without FastAPI or a database. Add useful parameter and return annotations while explaining the actual enforcement point. Prefer ordinary functions and standard-library tools until another abstraction has a clear purpose.

Teach resource cleanup with context managers when opening files or connections. Keep request data out of module-level mutable containers except clearly labeled local scaffolding. Teach timezone-aware instants, explicit date/time boundaries, and exact monetary representation when the domain requires them; do not add those topics to unrelated exercises.

Introduce async through waiting and the actual I/O library. Python async is not automatic CPU parallelism, and wrapping a blocking call in an async function does not make it nonblocking.

## Practice and review

Ask for a prediction, a short runnable experiment, and an explanation of the result. Specify data, expected values or exception behavior, and how to run the check. Use simple assertions initially and the project's chosen test runner once introduced. Include invalid input and repeated-call cases when relevant.

Review whether the learner can identify the enforcing line, explain state lifetime, and change a rule independently. Consult learning/PROGRESS.md before assuming proficiency. Do not count assistant-generated solutions or simulated evaluations as learner evidence.

## Reading and adaptive assessment

Follow learning/TEACHING.md and the current concept queue. Read short functions before writing related changes: predict bindings/mutation, branches/errors, and return values, then explain why. Use a fresh input or nested-container case when appropriate to test the mental model. If only spelling is missing, keep the conceptual task and offer a reference; if execution is misunderstood, model a trace and retry. Record code reading, concepts, implementation/testing, and documentation use separately. Assistant-run examples are not learner evidence.
