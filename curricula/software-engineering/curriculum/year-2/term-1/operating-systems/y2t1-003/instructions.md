# Threads, Synchronization and Concurrency Bugs

**Task ID:** `y2t1-003`  
**Estimated effort:** 20 hours  
**Module:** Operating Systems

## Why this task exists

Experience races, locks, deadlocks and coordination rather than only reading definitions.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **MIT 6.1810 - Operating System Engineering** (primary): https://pdos.csail.mit.edu/6.1810/

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Create a deliberately racy counter/work-queue program.
2. Reproduce the race and explain why it is nondeterministic.
3. Fix it using appropriate synchronization.
4. Construct a small deadlock example, then eliminate it using a documented lock-order rule.
5. Compare threads with processes and async I/O.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] Race is reproducible under stress.
- [ ] Fix is tested.
- [ ] Deadlock cause is explained with wait relationships.
- [ ] Apprentice can state an invariant protected by each lock.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. Why can adding a lock still produce incorrect software?
2. What makes concurrency bugs difficult to reproduce?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Introduce a second shared variable during review and ask how invariants change.

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
