# Consume a Stream Without Losing or Double-Writing

**Task ID:** `de1t2-003`
**Estimated effort:** 10 hours
**Module:** Streaming

## Why this task exists

Batch watermarks were a cursor over files or tables. A stream gives you
acks and offsets instead. The failure mode is the same: commit the cursor
before the write and you drop; write without a unique `event_id` and you
double.

Kafka is the default (a log you can replay). RabbitMQ is the contrast (a
queue you ack). Pick one to implement. Read the other far enough to write
three honest sentences about what replay would change.

## Authoritative resources

- **Apache Kafka Documentation** (primary if you implement Kafka):
  https://kafka.apache.org/documentation/
  — consumers, offsets, at-least-once, idempotence on the producer is
  optional; your sink must still be idempotent.
- **RabbitMQ Tutorials** (primary if you implement RabbitMQ; required
  contrast either way): https://www.rabbitmq.com/tutorials
  — acknowledgements and what happens when a consumer dies.
- **Python 3 Tutorial** (reference): https://docs.python.org/3/tutorial/
- **PostgreSQL Documentation** (reference): https://www.postgresql.org/docs/current/

Use official documentation as the primary source. If you use anything else,
record it in your notes. Local Kafka (KRaft or Docker) or a local RabbitMQ
is expected. You do not need a cluster.

## Work to complete

1. Produce at least 200 events, each with a stable `event_id`. Consume
   them into PostgreSQL with a uniqueness constraint (or equivalent) on
   `event_id`.
2. Commit the Kafka offset or ack the RabbitMQ message only after the
   warehouse write returns success. Comment the order in code.
3. Crash after a successful write and before the ack/offset commit.
   Restart the consumer. Distinct `event_id` count must equal distinct
   produced events, not more.
4. Replay from an earlier offset, or force redelivery. Distinct `event_id`
   count must not increase. Capture a duplicate insert attempt that fails
   or no-ops.
5. Write a queue-versus-log note of at least three sentences naming both
   Kafka and RabbitMQ: what you can replay, what you ack, and what that
   does to a warehouse sink.

## Required evidence

- Producer and consumer code plus the warehouse uniqueness constraint on
  `event_id`
- A captured duplicate-insert attempt that fails or no-ops
- A crash-before-ack demonstration and the post-restart distinct
  `event_id` count
- A replay or redelivery run whose distinct `event_id` count does not
  increase
- A queue-versus-log note of at least three sentences naming both Kafka
  and RabbitMQ
- Reflection notes answering the questions below

Submit a repository URL plus a commit reference. Broker logs alone are
not warehouse evidence.

## Acceptance criteria

- [ ] The warehouse has a uniqueness constraint or equivalent on
      `event_id`, and a duplicate insert attempt fails or is a no-op,
      shown in a captured statement.
- [ ] The consumer commits the Kafka offset or acks the RabbitMQ message
      only after the warehouse write returns success, shown by code order
      plus a crash-before-ack demonstration.
- [ ] After crash-before-ack and restart, the warehouse `event_id` count
      equals the number of distinct produced events, not more.
- [ ] A replay from an earlier offset or a queue redelivery does not
      increase the distinct `event_id` count.
- [ ] A notes file contains a queue-versus-log comparison of at least
      three sentences that names both Kafka and RabbitMQ.

The mentor may ask you to ack first on purpose and say what warehouse
state that would create. If you cannot, the order is accidental.

## Reflection

Answer these in your own words after doing the work:

1. What did you lose by choosing at-least-once plus an idempotent sink
   instead of exactly-once end to end?
2. If you had used the other broker, which of your demonstrations would
   have been harder, and why?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you learned the objective?

## Mentor review guide

Ask the apprentice to point at the ack/commit line and the write line and
to name the window where a crash duplicates work. Do not approve a
consumer that stores offsets only in memory.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is
not the intended path for this task. The apprentice must be able to
reproduce crash-before-ack without the model. Material AI assistance must
be recorded in the submission notes with the provider/model (if known),
purpose, and verification performed.

## Completion gate

This task is not complete when 200 events land once. It is complete once
the constraint, crash-before-ack, replay, and queue-versus-log note are
submitted and the mentor approves the demonstrated competency.
