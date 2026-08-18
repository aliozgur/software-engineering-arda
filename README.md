# apprenti.dev Software Engineering Apprenticeship

A forkable, evidence-driven four-year software-engineering apprenticeship designed to complement a strong
Mathematics/Computer Science university education.

> **Git fork model.** This repository is **curriculum**. After you fork it, apprenti.dev writes apprentice and mentor records only under `learners/` and `mentors/`. The app does not publish or clean a fork. If you copy or share your fork as a new base, **remove those two folders first** — Git history can still contain them. Details: [docs/GIT_FORK_MODEL.md](docs/GIT_FORK_MODEL.md).

## Core idea

**Learn -> Build -> Prove -> Reflect -> Review**

This is not an LMS export and not a playlist. Each task contains authoritative resources, practical work,
required evidence, acceptance criteria, reflection questions, mentor review guidance and an AI-use policy.

## Curriculum scale

- 54 detailed apprenticeship tasks
- 29 competency areas
- 32 curated primary/reference resources
- 4 academic years plus summer practice
- milestone projects, mentor challenges, open-source work and a final capstone

## Repository roles

The upstream repository contains canonical curriculum definitions. A learner/mentor pair should **fork** it and
record learner state, submissions, reflections and mentor reviews in their fork. Curriculum files and learner-owned
files should remain separate to reduce Git merge conflicts.

Suggested fork additions:

```text
learners/<learner-id>/profile.json
learners/<learner-id>/tasks/<task-id>/state.json
learners/<learner-id>/tasks/<task-id>/reflection.md
learners/<learner-id>/tasks/<task-id>/evidence.md
learners/<learner-id>/tasks/<task-id>/notes/<note-id>.json
learners/<learner-id>/tasks/<task-id>/notes/<note-id>.md
learners/<learner-id>/tasks/<task-id>/worklog.json
learners/<learner-id>/submissions/<submission-id>.json
mentors/<mentor-id>/reviews/<review-id>.json
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
4. Begin with `curriculum/year-1/term-1/...`.
5. Fork the repository before recording learner-specific progress.
6. Read `docs/LEARNER_NOTES.md` before writing notes in the fork.
