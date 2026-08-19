# apprenti.dev apprenticeship curricula

This repository is a **forkable curriculum working copy**. It currently ships two curricula:

| Curriculum | Manifest | Path |
|---|---|---|
| Software Engineering Apprenticeship (4 years, 54 tasks) | [curricula/software-engineering/curriculum.json](curricula/software-engineering/curriculum.json) | `curricula/software-engineering/` |
| Data Analytics and AI Apprenticeship (Year 1 + Year 2 Term 1, 19 tasks) | [curricula/data-analytics-ai/curriculum.json](curricula/data-analytics-ai/curriculum.json) | `curricula/data-analytics-ai/` |

The ordered list is [curricula.json](curricula.json). apprenti.dev treats each manifest as a selectable curriculum in the same Git repo. Shared `resources/`, `competencies/`, and `schemas/` live **once at the repository root**. A nested `curricula/<slug>/competencies/` or `resources/` folder is an optional **override** of the same id, not a second library. Software Engineering and Data Analytics both inherit the root libraries.

> **Git fork model.** After you fork, apprenti.dev writes apprentice and mentor records only under `learners/` and `mentors/`. Nested-curriculum overlays use `learners/<id>/c/<curriculum-id>/`. The app does not publish or clean a fork. If you copy or share your fork as a new base, **remove those two folders first** — Git history can still contain them. Details: [docs/GIT_FORK_MODEL.md](docs/GIT_FORK_MODEL.md).

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
4. Software Engineering: begin with `curricula/software-engineering/curriculum/year-1/term-1/...`. Data Analytics and AI: begin with `curricula/data-analytics-ai/curriculum/year-1/term-1/...`.
5. Fork the repository before recording learner-specific progress. Both curricula share that fork.
6. Read `docs/LEARNER_NOTES.md` before writing notes in the fork.
