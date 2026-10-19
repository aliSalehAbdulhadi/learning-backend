# Concepts and review queue

This is the current evidence index; [HISTORY.md](HISTORY.md) preserves the attempts behind it. Follow [TEACHING.md](TEACHING.md). Add backend concepts as they become relevant rather than preloading the whole course.

## Evidence states

- **Not assessed:** no usable learner performance yet; not a failing score.
- **Needs work:** an assessed attempt shows an unresolved misconception or incorrect behavior; name the gap and keep the attempt as evidence.
- **Supported:** demonstrated with a hint, model, or worked solution; name the help.
- **Independent now:** demonstrated on a fresh comparable task without solution guidance or a conceptual hint. Documentation lookup is allowed and recorded. Repeating a just-corrected example is still supported evidence.
- **Retained/transferred:** retrieved after a meaningful delay and/or applied independently to a changed case. State which occurred: immediate transfer does not demonstrate delayed retention.

Apply states separately to concept reasoning, code reading, implementation/testing, and documentation use. One dimension does not automatically advance another. A later misconception can change the current state while earlier evidence remains in history.

## Active concepts

| ID | Concept / decision to understand | Current evidence | Last attempt | Next review trigger |
| --- | --- | --- | --- | --- |
| PY-BINDING | Two names can refer to the same mutable object | Not assessed in all dimensions | — | Introduce with first reading task; no review scheduled |
| PY-COLLECTIONS | Sets represent membership; dictionaries map keys to values | Not assessed in all dimensions | — | Teach/check as needed by the trace and Exercise 01 |
| PY-COPY | A shallow copy creates a new outer container and can share nested values | Not assessed in all dimensions | — | After assignment/mutation is understood |
| PY-TYPES | Hints, runtime validation, and operations provide different guarantees | Not assessed in all dimensions | — | Short typed-function prediction before Exercise 01 |
| PY-ERRORS | Deliberate failure differs from a successful return | Not assessed in all dimensions | — | When introducing the first domain rule |
| PY-FUNCTIONS | Read parameters, return values, indentation, and imports | Not assessed in all dimensions | — | Explain enough syntax for the current snippet |
| READ-TRACE | Trace input, state, branches/errors, and output; summarize purpose | Not assessed in all dimensions | — | First Lesson 01 diagnostic |
| DOC-LOOKUP | Name the concept, locate version-matched docs, apply and verify | Not assessed in all dimensions | — | First genuine syntax/API lookup during practice |

For an assessed concept, replace its summary with dimension states and evidence links, for example `concepts: supported (S-.../Q-...); reading: independent now (...); implementation: not assessed; docs: independent now (...)`. This is a format example, not a learner result.

## Scheduling and concept notes

After practice, record the last attempt and next-session trigger or actual date in Baghdad time. Next session, roughly a week, then a few weeks are initial heuristics; shorten after conceptual errors and extend after delayed success. Select a small useful review at a time. Untouched concepts get no due date; overdue dates are not failure.

Add a short learner-authored note when useful: the idea in their words, when useful, a limit/counterexample, and search terms for details. Assistant-written notes are references, not proof of understanding. Leave unknowns unassessed.
