# Exercise 01 — Python domain rules

**Goal:** implement and verify one backend rule in ordinary Python before adding HTTP or a database.

Allow **45–60 minutes** for a first attempt. If Python syntax is slowing you down, ask for a small unrelated example or a hint; finishing every extension today is unnecessary.

## The problem

A team owns equipment. A known member may check out a known piece of equipment if nobody currently has it. Each equipment item can have at most one active borrower.

For this exercise, members are assumed to belong to the same team. Authentication, team permissions, persistence, and concurrent requests come in later milestones. This is local, single-process practice.

## Prerequisites

Use functions, dictionaries, sets, type hints, exceptions, and simple assertions. You already know the programming concepts; focus on how Python expresses them.

Before implementing, be able to explain dictionary lookup, set membership, `None`, and how to raise and catch an exception. If one is unfamiliar, ask for that explanation first.

Python **3.14.6** was available when this workspace was created. Confirm your current interpreter with `python3 --version`. No third-party packages are needed. The [Python 3.14 tutorial](https://docs.python.org/3.14/tutorial/) covers functions, data structures, errors, modules, and environments; use the documentation matching your interpreter.

## Your task

Create `checkout.py` in this exercise directory. Implement this interface; the body is yours:

```python
def checkout(
    equipment_ids: set[int],
    member_ids: set[int],
    active_loans: dict[int, int],
    equipment_id: int,
    member_id: int,
) -> dict[int, int]:
    ...
```

`active_loans` maps an equipment ID to its current borrower's member ID. Accept integer IDs as a precondition for this first exercise; runtime input validation is a later extension.

On success, return a **new dictionary** containing the existing loans plus the new loan. Leave the input dictionary unchanged. This makes state changes and failed operations easy to inspect.

Raise `ValueError` with one of these messages when a rule fails, checking in the order shown:

1. Unknown equipment → `equipment_not_found`
2. Unknown member → `member_not_found`
3. Equipment already borrowed → `equipment_unavailable`

Repeated checkout of borrowed equipment must fail even when the requester is the current borrower. That is this exercise's explicit rule; we will revisit retries later.

## Examples and checks

Start each case from the specified state, using equipment IDs `{101, 102}` and member IDs `{7, 8}`.

| Existing loans | Request: equipment, member | Expected outcome |
| --- | --- | --- |
| `{}` | `101, 7` | Return `{101: 7}`; original remains `{}` |
| `{101: 7}` | `102, 8` | Return `{101: 7, 102: 8}`; original unchanged |
| `{101: 7}` | `101, 8` | Raise `ValueError("equipment_unavailable")` |
| `{101: 7}` | `101, 7` | Raise `ValueError("equipment_unavailable")` |
| `{}` | `999, 7` | Raise `ValueError("equipment_not_found")` |
| `{}` | `101, 999` | Raise `ValueError("member_not_found")` |
| `{101: 7}` | `101, 999` | Raise `ValueError("member_not_found")` |
| `{}` | `999, 999` | Raise `ValueError("equipment_not_found")` |

Create `check_checkout.py` beside your implementation. Import the function and check these cases with assertions and exception handling. Check unchanged input on both successful and failing calls. If an expected exception never occurs, make that check fail explicitly; catching an exception by itself is not enough.

From this directory, run `python3 check_checkout.py`. From the project root, run `python3 exercises/01-python-domain-rules/check_checkout.py`. These commands apply after you create the two files.

## Explain your result

After the code works, answer these in your own words:

1. Which lines enforce the business rules? Do the annotations enforce them?
2. Why return a new dictionary? Which behavior would change if you mutated the input instead?
3. What happens to this state when the process restarts?
4. If two servers both start with an empty loan map, can this function alone guarantee one borrower across both servers? Explain without implementing a database solution yet.

You are done when the checks pass, you can explain these answers, and you can change one rule without copying a solution. Share the code and actual command output for review.

## Optional follow-up

Only after the core exercise: implement a return operation, or design validation for values coming from JSON. For validation, decide what to do with `"101"`, `None`, and `True`; do not assume annotations enforce your choice. See [Python's type-hint documentation](https://docs.python.org/3.14/library/typing.html) for that distinction.

After review, finish the remaining M1 work in the [roadmap](../../learning/ROADMAP.md): return and availability behavior, environment practice, and the request lifecycle. Then M2 will expose a small operation through FastAPI and deliberately map success and failure into HTTP responses.
