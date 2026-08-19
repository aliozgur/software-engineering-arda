# Milestone 2: Networked Service Under Failure

**Task ID:** `y2t2-007`  
**Estimated effort:** 32 hours  
**Module:** Milestone

## Why this task exists

Integrate systems knowledge by building a service that behaves predictably under failure.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- No single mandatory external course. Use official documentation and mentor-curated references appropriate to the task.

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Design a client/server service with a documented protocol or HTTP contract.
2. Add concurrency, timeouts and cancellation.
3. Containerize it and automate tests in CI.
4. Inject failures: client disconnect, server restart, slow dependency and malformed input.
5. Create an operations runbook and a short architecture diagram.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] Failure cases have defined behavior.
- [ ] No unbounded waits in tested paths.
- [ ] Logs make failures diagnosable.
- [ ] Release can be reproduced from tag.
- [ ] Demo includes at least two injected failures.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. Which failure changed your architecture?
2. What did the OS/networking knowledge let you diagnose faster?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Conduct a failure-injection demo rather than a happy-path demo.

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
