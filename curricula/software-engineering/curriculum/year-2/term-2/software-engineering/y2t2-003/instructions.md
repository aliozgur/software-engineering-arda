# Modularity, Refactoring and Architecture

**Task ID:** `y2t2-003`  
**Estimated effort:** 18 hours  
**Module:** Software Engineering

## Why this task exists

Recognize design quality through changeability rather than pattern vocabulary.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- No single mandatory external course. Use official documentation and mentor-curated references appropriate to the task.

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Take an intentionally tangled application or an older project.
2. Identify responsibilities, coupling and change hotspots.
3. Add characterization tests before refactoring.
4. Refactor toward clearer module boundaries.
5. Write an ADR explaining one architecture decision and rejected alternatives.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] Behavior remains covered by tests.
- [ ] Refactoring commits are separate from feature changes.
- [ ] ADR contains context, decision, consequences and alternatives.
- [ ] Apprentice can explain why the new structure makes a named change easier.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. Which coupling caused the most pain?
2. What abstraction did you remove rather than add?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Request a new feature after refactor; evaluate whether claimed boundaries help.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that
force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, quizzes and review unless the mentor further restricts it. Solution generation
is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must
be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the
mentor approves the demonstrated competency.
