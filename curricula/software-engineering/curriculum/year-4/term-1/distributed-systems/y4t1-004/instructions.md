# Idempotency, Sagas and Distributed Workflows

**Task ID:** `y4t1-004`  
**Estimated effort:** 18 hours  
**Module:** Distributed Systems

## Why this task exists

Design business workflows that span components without pretending there is one global transaction.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- No single mandatory external course. Use official documentation and mentor-curated references appropriate to the task.

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Design a multi-step workflow such as order/payment/provisioning in a sandbox domain.
2. Define idempotency keys and duplicate handling.
3. Implement compensating actions for at least one failed step.
4. Persist workflow state.
5. Test retries, out-of-order events and partial failure.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] State machine is documented.
- [ ] Every retryable command/event has duplicate semantics.
- [ ] Compensation limitations are acknowledged.
- [ ] Failure tests preserve stated invariants.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. Why isn't compensation the same as rollback?
2. Where could a message be lost between database commit and publish?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask apprentice to discuss transactional outbox as a possible solution and its trade-offs.

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
