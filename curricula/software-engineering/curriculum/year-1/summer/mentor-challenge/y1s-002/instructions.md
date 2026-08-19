# Mentor Challenge: Diagnose a Slow Query

**Task ID:** `y1s-002`  
**Estimated effort:** 8 hours  
**Module:** Mentor Challenge

## Why this task exists

Practice investigation without a tutorial-shaped solution.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **PostgreSQL Documentation** (reference): https://www.postgresql.org/docs/current/

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Mentor supplies a PostgreSQL schema/data set and a slow query.
2. Form hypotheses before changing anything.
3. Measure with EXPLAIN ANALYZE.
4. Apply one or more changes and re-measure.
5. Write an incident-style diagnosis with evidence and trade-offs.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] Before/after measurements are present.
- [ ] Changes are justified.
- [ ] No 'add indexes everywhere' solution.
- [ ] Report separates observations, hypotheses, experiments and conclusion.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. Which hypothesis was wrong?
2. What additional production data would you want?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Do not reveal the intended fix early.
- Score investigation quality as heavily as final performance.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that
force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **hint_only**

AI may be used for explanation, hints, quizzes and review unless the mentor further restricts it. Solution generation
is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must
be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the
mentor approves the demonstrated competency.
