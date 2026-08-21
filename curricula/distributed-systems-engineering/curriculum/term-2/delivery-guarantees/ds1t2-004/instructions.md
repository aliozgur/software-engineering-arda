# RabbitMQ Ack Windows, Broker Restart, and a Poison Message

**Task ID:** `ds1t2-004`
**Estimated effort:** 16 hours
**Module:** Delivery Guarantees

## Objective

Operate RabbitMQ locally with durable queues. For four named failures —
consumer crash before ack, consumer crash after the side-effect, broker
restart while a message is unacked, and a poison message that never
succeeds — write a prediction, run the failure, and record how many times
the domain effect ran. Then add one comparison sentence per row against
the Kafka offset-commit window you already saw.

## Why this task exists

The SWE messaging task builds acknowledgements, bounded retries, a DLQ,
and an idempotent consumer. Those are necessary and still leave the hard
question unanswered: *when* do you ack relative to the side-effect, and
what does a broker restart do to a message you have not acked? This task
fills that table. "At-least-once" is then a set of measured windows, not
a word Kafka and RabbitMQ both get to claim.

## Authoritative resources

- **RabbitMQ Tutorials** (primary): https://www.rabbitmq.com/tutorials
  — work through the official tutorials on work queues, acknowledgements,
  durability, and dead-lettering, then leave the tutorial code behind.
- **Docker Get Started** (reference): https://docs.docker.com/get-started/
  — run the broker in Compose so a restart is a command, not a myth.

## Setup notes

- A real RabbitMQ broker. An in-process fake is not acceptable.
- Queues and publishes must be durable (`durable: true`, persistent
  publish). A restart that empties the queue fails the third row.
- Prefetch must be explicit and stated. `autoAck=true` is allowed only as
  a contrast run you label; the four required rows use manual ack.
- You may reuse the domain side-effect table from `ds1t2-003`.

## Work to complete

1. Declare a durable queue, a dead-letter queue (or dead-letter exchange),
   and a publisher that sends persistent messages with a stable
   `event_id`. Write a consumer that performs a visible side-effect
   (insert a row, append a file) and then acks. Commit topology first.
2. **Before any failure run**, write the four predictions (what happens
   to the message, how many times the side-effect runs). Commit or
   timestamp that file.
3. Run the four failures:
   - **Crash before ack:** kill the consumer after receive, before
     side-effect and ack. Restart consumer. Record deliveries and
     effects.
   - **Crash after side-effect:** kill after the side-effect, before
     ack. Restart. Record whether the effect ran twice or was
     suppressed by an idempotency key — say which.
   - **Broker restart, unacked:** deliver a message, do not ack, restart
     the broker, restart the consumer. Show the message is still there
     (or record the loss if your durability was wrong, and fix it, and
     rerun).
   - **Poison:** publish a message your handler always fails. Bound the
     retries (application count or broker policy). Show the message on
     the DLQ and show the retry count is finite.
4. Write a results table with predicted vs actual vs effect count (0, 1,
   or N) for each row.
5. For each row, add one sentence comparing it to Kafka: offset commit
   before vs after the side-effect, and an uncommitted produce versus an
   unacked RabbitMQ message. No "Kafka is better" or "RabbitMQ is
   simpler."
6. `README.md` must state prefetch, ack mode, retry limit (a number),
   and the actual guarantee. The phrase "exactly-once" may appear only
   as something you are **not** claiming.

## Evidence you'll submit

- Compose and git history of durable topology first.
- The prediction file (committed or timestamped before runs) and the
  results table.
- Poison-path logs showing the DLQ and the retry bound.
- `README.md` and reflection notes.

## Acceptance criteria

- [ ] All four failure classes are run against a durable queue and a
      durable published message; the table has a predicted column
      committed or timestamped before the corresponding run.
- [ ] Crash-after-side-effect shows the domain effect occurring more
      than once unless an idempotency key suppresses the second apply —
      and the table says which of those two you implemented.
- [ ] The poison message appears on an inspectable dead-letter queue
      after at most the configured retry count, and that count is a
      number in README and in the broker policy or application retry
      loop.
- [ ] README compares each of the four rows to the equivalent Kafka
      failure in one sentence per row — not a brand preference.

## Reflection

Answer in your own words after doing the work:

1. If you ack before the side-effect, which of the four rows becomes a
   silent drop instead of a duplicate? Would you accept that?
2. What does a RabbitMQ ack guarantee that a Kafka offset commit does
   not, and the other way around? Stay inside the four rows.

Also record: what took longer than expected, and what remains unclear
about prefetch versus "we will not lose this message."

## Mentor review guide

If a mentor reviews this work, kill the consumer at a fifth moment the
apprentice did not list and ask them to extend the table live. Do not
approve `autoAck` on the required rows or a DLQ that was never read.

Suggested review outcome: **Approve**, **Request revision**, or **Create
follow-up challenge**.

## AI use policy

Mode: **guided**. Explain, hint, and quiz are available; solution
generation is not. Disclose any material AI use with provider/model,
purpose, and verification performed.

## Completion gate

This task is complete only after the evidence is submitted and, when a
mentor is present, the mentor approves the demonstrated competency.
Tutorial completion is preparation, not evidence.
