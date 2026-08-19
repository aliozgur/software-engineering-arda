# Kafka Concepts and Event Logs

**Task ID:** `y3t1-007`  
**Estimated effort:** 12 hours  
**Module:** Event Streaming

## Why this task exists

Understand the difference between a queue-centric broker and a partitioned durable event log.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **Apache Kafka Documentation** (deep_dive): https://kafka.apache.org/documentation/

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Study Kafka concepts: topic, partition, offset, consumer group, retention.
2. Run a local Kafka-compatible lab if practical.
3. Produce keyed events and observe partitioning/consumer groups.
4. Compare RabbitMQ and Kafka for three concrete scenarios.
5. Document replay and ordering boundaries.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] Comparison is scenario-based, not brand-based.
- [ ] Apprentice can explain offset and consumer group.
- [ ] Ordering claims are scoped to partitions.
- [ ] Replay implications for consumers are understood.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. Why is a log useful beyond messaging?
2. What changes when consumers control their offsets?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Give a workload and ask apprentice to choose RabbitMQ, Kafka or neither.

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
