# Learning backend

A practical backend learning workspace for an experienced frontend developer. The goal is to build and operate a small API while understanding the guarantees behind it.

The stack is **Python → FastAPI → PostgreSQL**. We will use a **team equipment checkout service** throughout: members borrow and return equipment, managers maintain inventory, and each team can access only its own data. The same backend can later serve an Expo app.

## Start here

1. Read the [learning roadmap](learning/ROADMAP.md). It builds on your programming and system design experience.
2. Work through [Exercise 01: Python domain rules](exercises/01-python-domain-rules/README.md), a 45–60 minute first attempt with no framework or database installation.
3. Share your attempt in chat for review. [Progress](learning/PROGRESS.md) records demonstrated understanding and the next step.

You have **6–10 hours per week**. Use four 90-minute sessions as a base, with the remaining time for practice or catching up. Advance when you can build, explain, and verify the milestone; there is no fixed graduation date.

## How we will learn

Short explanation → small exercise → your attempt → targeted feedback → revisit later.

You can ask for a hint, an explanation, a quiz, code review, or a complete worked solution. Guided practice is the default. Exercises stay unsolved until you attempt them or ask for the answer.

Useful starting messages:

- “Start Exercise 01. Explain the Python differences I need, then let me implement it.”
- “Review my solution for correctness and reasoning before style.”
- “Give me one hint for the failing case.”
- “Quiz me on the last milestone using a new example.”
- “Show a complete solution and explain the tradeoffs.”

## Rules and skills

[AGENTS.md](AGENTS.md) contains the learner profile, teaching contract, backend engineering standards, and your Context7 documentation rules.

| Project-local skill | Focus |
| --- | --- |
| [backend-mentor](.agents/skills/backend-mentor/SKILL.md) | Teaching, exercises, feedback, and backend foundations |
| [python-backend-learning](.agents/skills/python-backend-learning/SKILL.md) | Python for an experienced JavaScript/TypeScript developer |
| [relational-database-learning](.agents/skills/relational-database-learning/SKILL.md) | SQL, tables, integrity, transactions, and query performance |
| [fastapi-backend-learning](.agents/skills/fastapi-backend-learning/SKILL.md) | HTTP APIs, validation, dependencies, security, and testing |

These custom skills are kept in the repository's `.agents/skills` directory, a supported [Codex skill location](https://developers.openai.com/codex/skills/#where-to-save-skills). They can be selected when relevant; AGENTS.md also routes lessons to their files. If they do not appear in the skill picker after creation, restart Codex. No global skill installation is needed.

The workspace currently contains the learning materials and instructions. Application code and dependencies will be added through the exercises.
