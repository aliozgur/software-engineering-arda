# apprenti.dev Software Engineering Apprenticeship

A forkable, evidence-driven four-year software-engineering apprenticeship designed to complement a strong
Mathematics/Computer Science university education.

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
learners/<learner-id>/submissions/<submission-id>.json
mentors/<mentor-id>/reviews/<review-id>.json
```

Notes, reflections and evidence notes are **fork-owned**. See [docs/LEARNER_NOTES.md](docs/LEARNER_NOTES.md).

## Persistence philosophy for apprenti.dev

The Git repository is the durable, human-readable source of truth. The mobile application may project/index this
content into SQLite for offline operation, search, AI embeddings, sync state and transient drafts. High-frequency UI
state and model runtime data should not be committed to Git.

## File formats

- JSON: structured domain objects
- Markdown: narrative/instructional/reflection content
- JSON Schema: validation contracts

## AI policy

AI is part of modern engineering, but the apprentice remains accountable. Tasks can be guided, restricted,
hint-only, brainstorming-only or fully allowed. Material AI use must be disclosed. Mentor approval requires the
apprentice to explain and modify the submitted work.

## Start here

1. Read `CURRICULUM_AUDIT.md`.
2. Read `docs/LEARNING_MODEL.md`.
3. Begin with `curriculum/year-1/term-1/...`.
4. Fork the repository before recording learner-specific progress.
5. Read `docs/LEARNER_NOTES.md` before writing notes in the fork.
