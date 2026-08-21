# apprenti.dev apprenticeship curricula

This repository is a **forkable curriculum working copy**. It ships two long-form reference apprenticeships and fourteen shorter specializations. The ordered list is [curricula.json](curricula.json). apprenti.dev treats each manifest as a selectable curriculum in the same Git repo.

Shared `resources/`, `competencies/`, and `schemas/` live **once at the repository root**. A nested `curricula/<slug>/competencies/` or `resources/` folder is an optional **override** of the same id, not a second library. Every curriculum below inherits the root libraries.

> **Git fork model.** After you fork, apprenti.dev writes apprentice and mentor records only under `learners/` and `mentors/`. Nested-curriculum overlays use `learners/<id>/c/<curriculum-id>/`. The app does not publish or clean a fork. If you copy or share your fork as a new base, **remove those two folders first** — Git history can still contain them. Details: [docs/GIT_FORK_MODEL.md](docs/GIT_FORK_MODEL.md).

## Reference apprenticeships

| Curriculum | Scale | Manifest |
|---|---|---|
| [Software Engineering](curricula/software-engineering/) | 4 years, 54 tasks | [curriculum.json](curricula/software-engineering/curriculum.json) |
| [Data Analytics and AI](curricula/data-analytics-ai/) | Year 1 + Year 2 Term 1, 19 tasks (v0.1 — later years not authored yet) | [curriculum.json](curricula/data-analytics-ai/curriculum.json) |

## Specializations

Shorter paths for people who already write software and want a mentor-reviewed pass through one craft. Durations are the designed range, not a promise.

| Curriculum | Designed for | Tasks | Path |
|---|---|---|---|
| [AI-Native Software Engineering](curricula/ai-native-software-engineering/) | Working developers, 4–6 months | 12 | `curricula/ai-native-software-engineering/` |
| [Backend Engineering](curricula/backend-engineering/) | Junior–mid, 9–12 months | 19 | `curricula/backend-engineering/` |
| [Software Architecture & System Design](curricula/software-architecture-system-design/) | Mid–senior, 6–9 months | 16 | `curricula/software-architecture-system-design/` |
| [Engineering Foundations for Junior Developers](curricula/engineering-foundations/) | New grads / juniors, 4–6 months | 14 | `curricula/engineering-foundations/` |
| [Platform / DevOps Engineering](curricula/platform-devops-engineering/) | SWE / ops, 6–9 months | 15 | `curricula/platform-devops-engineering/` |
| [Distributed Systems Engineering](curricula/distributed-systems-engineering/) | Mid/senior backend, 4–6 months | 11 | `curricula/distributed-systems-engineering/` |
| [Data Engineering](curricula/data-engineering/) | SWE / analytics engineer, 6–9 months | 15 | `curricula/data-engineering/` |
| [Application Security Engineering](curricula/application-security-engineering/) | Software engineers, 4–6 months | 12 | `curricula/application-security-engineering/` |
| [Software Quality & Test Engineering](curricula/software-quality-test-engineering/) | Developers / QA, 4–6 months | 10 | `curricula/software-quality-test-engineering/` |
| [Engineering Leadership](curricula/engineering-leadership/) | Senior / tech lead, 4–6 months | 9 | `curricula/engineering-leadership/` |
| [Performance Engineering](curricula/performance-engineering/) | Experienced engineers, 3–4 months | 8 | `curricula/performance-engineering/` |
| [Observability & Production Engineering](curricula/observability-production-engineering/) | Backend / platform, 3–4 months | 8 | `curricula/observability-production-engineering/` |
| [Open Source Engineering](curricula/open-source-engineering/) | Junior–senior, 2–3 months | 7 | `curricula/open-source-engineering/` |
| [Industrial / Edge Software Engineering](curricula/industrial-edge-software-engineering/) | Embedded / IIoT / backend, 6–9 months | 14 | `curricula/industrial-edge-software-engineering/` |

Data Engineering is the engineering of data movement (pipelines, contracts, orchestration). It is not a copy of Data Analytics and AI.

## Core idea

**Learn -> Build -> Prove -> Reflect -> Review**

This is not an LMS export and not a playlist. Each task contains authoritative resources, practical work,
required evidence, acceptance criteria, reflection questions, mentor review guidance and an AI-use policy.

## Curriculum scale

**Software Engineering**

- 54 detailed apprenticeship tasks
- Shared plus engineering competency areas
- 4 academic years plus summer practice
- milestone projects, mentor challenges, open-source work and a final capstone

**Data Analytics and AI** (v0.1)

- 19 tasks: Year 1 (two terms + summer) and Year 2 Term 1
- Analytics, inference, first models, then LLM/retrieval with eval
- Later years not authored yet — see [curricula/data-analytics-ai/README.md](curricula/data-analytics-ai/README.md)

**Specializations**

- 170 tasks across the fourteen paths above
- Each path reuses root competencies by id; a few add a genuinely new competency in their own folder (`data-pipelines`, `technical-leadership`, `incident-response`, `embedded-and-edge-systems`, and similar)
- Mentorship is optional on the specializations (`mentorship: "optional"` in each manifest)

## Repository roles

The upstream repository contains canonical curriculum definitions. A learner/mentor pair should **fork** it and
record learner state, submissions, reflections and mentor reviews in their fork. Curriculum files and learner-owned
files should remain separate to reduce Git merge conflicts.

Suggested fork additions:

```text
learners/<learner-id>/profile.json
learners/<learner-id>/c/<curriculum-id>/tasks/<task-id>/state.json
learners/<learner-id>/c/<curriculum-id>/tasks/<task-id>/reflection.md
learners/<learner-id>/c/<curriculum-id>/tasks/<task-id>/evidence.md
learners/<learner-id>/c/<curriculum-id>/tasks/<task-id>/notes/<note-id>.json
learners/<learner-id>/c/<curriculum-id>/tasks/<task-id>/notes/<note-id>.md
learners/<learner-id>/c/<curriculum-id>/tasks/<task-id>/worklog.json
learners/<learner-id>/c/<curriculum-id>/submissions/<submission-id>.json
mentors/<mentor-id>/c/<curriculum-id>/reviews/<review-id>.json
```

Notes, reflections, evidence notes and work logs are **fork-owned**. See [docs/LEARNER_NOTES.md](docs/LEARNER_NOTES.md) and [docs/GIT_FORK_MODEL.md](docs/GIT_FORK_MODEL.md).

If you copy or publish this fork yourself, **remove `learners/` and `mentors/`** first. The app will not do that. Git history can still contain those files until you start a new repository or rewrite history.

## Persistence philosophy for apprenti.dev

The Git repository is the durable, human-readable source of truth. The mobile application may project/index this
content into SQLite for offline operation, search, AI embeddings, sync state and transient drafts. High-frequency UI
state and model runtime data should not be committed to Git.

## File formats

- JSON: structured domain objects
- Markdown: narrative/instructional/reflection content
- JSON Schema: validation contracts
- Locale overlays: sibling `{stem}.{locale}.{ext}` next to the canonical file (e.g. `instructions.tr.md`). See [docs/CONTENT_LOCALES.md](docs/CONTENT_LOCALES.md). Canonical files stay English (`sourceLocale`). Do not reuse `curriculum.json` `languages` for human locales.

Every curriculum in this repository ships English plus Turkish sibling overlays (`contentLocales`: `en`, `tr`). Canonical files stay English.

`curriculum.json` may declare `progression`:

- `sequential` — submit earlier path tasks before later ones. This repository uses sequential order (year / term / summer from each `term.json`).
- `random` — tasks may be submitted in any order. This is the default when the field is omitted.

## AI policy

AI is part of modern engineering, but the apprentice remains accountable. Tasks can be guided, restricted,
hint-only, brainstorming-only or fully allowed. Material AI use must be disclosed. Mentor approval requires the
apprentice to explain and modify the submitted work.

## Start here

1. Read `CURRICULUM_AUDIT.md`.
2. Read `docs/LEARNING_MODEL.md`.
3. Read `docs/GIT_FORK_MODEL.md` before putting personal files in a fork.
4. Pick a curriculum from the tables above. Software Engineering starts at `curricula/software-engineering/curriculum/year-1/term-1/`. Data Analytics and AI starts at `curricula/data-analytics-ai/curriculum/year-1/term-1/`. Each specialization has its own `curriculum/` folder under `curricula/<slug>/`.
5. Fork the repository before recording learner-specific progress. Every curriculum in this repo shares that fork.
6. Read `docs/LEARNER_NOTES.md` before writing notes in the fork.
