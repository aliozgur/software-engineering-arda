# RabbitMQ: Reliable Messaging

**Task ID:** `y3t1-006`  
**Estimated effort:** 18 hours  
**Module:** Messaging

## Why this task exists

Build asynchronous workflows while confronting delivery semantics.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **RabbitMQ Tutorials** (reference): https://www.rabbitmq.com/tutorials

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Complete relevant RabbitMQ tutorials.
2. Build producer/consumer workflow with durable messages where appropriate.
3. Implement acknowledgements, retry policy and dead-letter handling.
4. Make consumer idempotent for a duplicated message.
5. Test consumer crash before/after side effect.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] Duplicate delivery does not corrupt domain state.
- [ ] Retry is bounded.
- [ ] Dead-letter messages are inspectable.
- [ ] README states actual delivery guarantee rather than claiming 'exactly once' casually.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. What does acknowledgement guarantee?
2. Where can duplicate side effects still occur?
3. Why can ordering disappear with multiple consumers?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Kill consumers at awkward times during demo.

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
