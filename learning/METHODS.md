# Learning methods and evidence

Research checked: **2026-10-19**. Scope: an adult senior frontend engineer learning Python, FastAPI, PostgreSQL, and backend ownership within 6–10 hours per week. This is a selective evidence-informed rationale, not a systematic review or a claim that one method is universally best.

[TEACHING.md](TEACHING.md) contains the working teaching agreement. [HISTORY.md](HISTORY.md) records decisions and sessions, [CONCEPTS.md](CONCEPTS.md) tracks concept evidence, and [PROGRESS.md](PROGRESS.md) holds the current position and next action. This document records reasons for the approach; it records no completed lesson or demonstrated learner success.

## Understand mechanisms, develop fluency, retrieve details

Our working approach combines three capabilities:

- **Conceptual understanding:** explain what happens, why it happens, where a guarantee is enforced, and what changes when assumptions fail. Backend examples include process memory versus durable state, validation versus database constraints, and identity versus permission.
- **Automatic basic literacy:** recognize and trace common syntax and control flow with increasing ease. Repeated use should make routine function calls, data access, exception handling, and simple queries less effortful. This means useful fluency, not memorizing every signature or command.
- **Documentation retrieval:** identify what is unknown, find the relevant current reference, apply it, and verify the result. Details that vary by library or version belong here; the project's documentation workflow governs those lookups.

This combination is our engineering inference, not a separately validated learning package. Its strength is that mechanisms can transfer while documentation supplies changing details. Its failure modes need active checks: explaining vocabulary can conceal weak execution knowledge; copying documented examples can conceal misunderstanding; looking up every basic operation can interrupt reasoning; memorizing syntax can produce fluent but incorrect code. Practice should address the observed gap rather than favoring one capability exclusively.

Frontend analogies help activate useful prior knowledge, but explicitly name their limits. A familiar component lifecycle does not establish knowledge of transactions, multiple worker processes, or authorization.

## Assess briefly and adapt continuously

Use a small diagnostic before unfamiliar material: explain a relationship, predict an outcome, trace a short example, or attempt a bounded change. Self-reported familiarity provides context; direct performance provides different evidence. CMU's Eberly Center recommends assessing prior knowledge and misconceptions, then adjusting instruction and complexity. This is **institutional teaching guidance**, not a causal experiment on this learner. [CMU, undated](https://www.cmu.edu/teaching/designteach/teach/priorknowledge.html)

An incorrect answer should trigger investigation: unfamiliar notation, a mistaken mechanism, missing prerequisite knowledge, or an unclear question may require different responses. Offer a hint or explanation and check again with a changed example. This is adaptive formative assessment; it is not a standardized diagnosis or a permanent ability label.

Finland's **2022 adult integration curriculum** calls for varied ongoing assessment and feedback, recognition of prior learning, and jointly updated personal study plans (printed pp. 24–25 and 52–53). These are useful **policy examples** for adult education. They do not establish Finnish educational superiority or demonstrate causal effects in adult programming instruction; the English document is an unofficial translation. [Finnish National Agency for Education](https://www.oph.fi/sites/default/files/documents/National_core_curriculum_for_integration_training_2022.pdf)

The agency's current **AI-assessment background guidance** also describes adapting assignment difficulty and providing feedback during practice, while reserving formal competence decisions for responsible educators. Our adaptation is formative coaching supported by observed answers and code, not institutional grading or certification. [Official AI and assessment guidance, accessed 2026-10-19](https://www.oph.fi/en/teemat-ja-kehittaminen/backround-material-ai-assessment-learning-and-competence)

## Read, reason, change, and build

A flexible practice sequence is:

1. **Predict** the result or failure before execution.
2. **Read and trace** the relevant code, data, and control flow.
3. **Run** it and compare observation with prediction.
4. **Explain** the mechanism and resolve any mismatch.
5. **Modify** one requirement or failure condition.
6. **Build** a bounded related solution with less support.
7. **Return later** to a changed problem and check transfer.

Use the steps that serve the objective; do not force every factual answer through this sequence. Give prerequisites, concrete inputs, expected outcomes, failure cases, and a verification method. Reading alone cannot establish building skill, and building alone can conceal weak understanding.

In a **2021 observational programming study**, Aalto researchers asked learners questions about their own submitted programs. Some passed functional tests while giving incorrect explanations. This supports checking reasoning alongside outputs; it does not prove that explanation questions cause better learning, and written expression can affect answers. [Lehtinen, Lukkarinen & Haaranen](https://arxiv.org/pdf/2104.06710)

When the mechanism is new, demonstrate a small different worked example, then provide partial support and gradually remove it. Experiments on probability learning found benefits from fading worked steps and prompting underlying principles; the prompts also supplied feedback. Applying this to backend mentoring is a **reasoned adaptation**, not direct adult-backend evidence. Avoid prolonged unguided struggle and fade support according to performance. [Atkinson, Renkl & Merrill, 2003](https://www.researchgate.net/publication/200772684_Transitioning_From_Studying_Examples_to_Solving_Problems_Effects_of_Self-Explanation_Prompts_and_Fading_Worked-Out_Steps)

Active participation has broader support: a **2014 meta-analysis of 225 undergraduate STEM studies** favored active learning over traditional lecturing. Its varied interventions and classroom population do not establish an exact mentoring recipe. Use short explanations to support consequential learner thinking: prediction, debugging, comparison, and implementation. [Freeman et al.](https://www.pnas.org/doi/full/10.1073/pnas.1319030111)

## Use quizzes and feedback to improve learning

Use short, low-stakes retrieval checks on material already encountered: recall an invariant, explain a failure, predict behavior, or justify a choice. Include earlier concepts occasionally. A **2021 meta-analysis of 222 classroom studies** found an average learning benefit from quizzing, with substantial variation and larger benefits when corrective feedback was provided. [Yang et al.](https://gwern.net/doc/psychology/spaced-repetition/2021-yang.pdf)

An occasional informal pop quiz is acceptable, but surprise itself is not an established source of benefit. Avoid trivia unrelated to the objective and exhausting interrogation. Correct errors, explain the relevant mechanism, and allow another attempt. Review behavior and reasoning before style; distinguish syntax help from conceptual help. A quiz score is one observation, not proof of independent backend ownership.

## Space review and check transfer

Revisit important concepts across sessions rather than relying on a single successful attempt. As a practical starting point, recall something from the previous session and return to an important idea in a later week. These intervals are **heuristics**; shorten or extend them according to recall, difficulty, and upcoming use.

A **2008 adult factual-memory experiment** found that useful spacing depended on how long information needed to be retained. It does not justify a universally optimal review timetable for programming. [Cepeda et al.](https://escholarship.org/content/qt0kp5q19x/qt0kp5q19x.pdf)

Check transfer by changing an input, requirement, or assumption and asking for a prediction and justification. Combine explanation with implementation and verification. Use realistic failure and concurrency scenarios after their prerequisites have been taught.

## Keep the approach accountable

Adapt to demonstrated knowledge, preferences, accessibility needs, and the task. Do not assign visual, auditory, or kinesthetic learning-style labels: the evidence does not justify matching instruction to such classifications. [Pashler et al., 2008 issue](https://people.uncw.edu/kozloffm/nolearningstylespdf.pdf)

Plain explanation is the default. Use occasional interactive HTML when changing state, timing, or competing actions makes a mechanism easier to inspect; visual novelty alone is insufficient reason.

Record what was observed, assistance used, unresolved misconceptions, and one next action. Keep **not assessed**, **needs work**, **supported**, **independent now**, and **retained/transferred** distinct, naming the actual retention or transfer evidence. Reassess later and revise the approach when it fails to support understanding or transfer. Generated code, delivered explanations, and this research update are not evidence of learner mastery.
