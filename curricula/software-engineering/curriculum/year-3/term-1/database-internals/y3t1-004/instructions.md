# Transactions, Concurrency and Recovery

**Task ID:** `y3t1-004`  
**Estimated effort:** 24 hours  
**Module:** Database Internals

## Why this task exists

Reason about correctness under concurrent database access and crashes.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **CMU 15-445/645 - Database Systems** (primary): https://15445.courses.cs.cmu.edu/
- **PostgreSQL Documentation** (reference): https://www.postgresql.org/docs/current/

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Study transaction/concurrency/recovery material.
2. Reproduce at least two isolation phenomena using concurrent PostgreSQL sessions.
3. Implement a small concurrent reservation/transfer workflow and make it correct.
4. Document optimistic versus pessimistic approaches.
5. Study WAL/recovery concepts and connect them to durability.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] Concurrency test can expose the naive bug.
- [ ] Correct version states its invariant.
- [ ] Isolation level choice is justified.
- [ ] Recovery note explains WAL at a conceptual level.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. Can serializable transactions still fail and require retry?
2. Why is application-level idempotency different from database atomicity?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Run concurrent requests during demo and inspect resulting invariants.

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
