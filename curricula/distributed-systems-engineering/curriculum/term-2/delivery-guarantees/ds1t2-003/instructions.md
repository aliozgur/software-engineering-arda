# Dual-Write Loss and a Transactional Outbox You Can Measure

**Task ID:** `ds1t2-003`
**Estimated effort:** 16 hours
**Module:** Delivery Guarantees

## Objective

Build a small service that writes a domain row to PostgreSQL and publishes
a matching event to Kafka. First do it as two independent writes and crash
between them so the row exists and the event does not. Then put the event
in an outbox table in the same database transaction, poll it out, and show
the same crash no longer loses the event. Instrument both paths with
OpenTelemetry so a mentor can see where the first path dies.

## Why this task exists

The SWE distributed-workflow task designs sagas and compensating actions.
This task is the failure those sagas still hit if the first step is
"commit then publish": the database tells the user yes, the log never
hears about it. You will make that lie, then replace it with a design
whose traces still complete after a kill.

## Authoritative resources

- **PostgreSQL Documentation** (primary): https://www.postgresql.org/docs/current/
  — transactions, `COMMIT`, and what is and is not atomic with a network
  call.
- **Apache Kafka Documentation** (primary): https://kafka.apache.org/documentation/
  — producers, acks, and consumer offsets. Do not lean on Kafka
  transactions as a substitute for the outbox unless you also still
  implement the outbox path.
- **OpenTelemetry Documentation** (primary): https://opentelemetry.io/docs/
  — traces, context propagation, and exporting spans (console or OTLP).

## Setup notes

- PostgreSQL and a Kafka-protocol broker, locally, under Compose or
  equivalent. The SWE saga sandbox is not a substitute.
- The crash must be a real process kill (`kill -9`, container stop) after
  `COMMIT` of the domain row and before a successful produce, or an
  injected fault that skips the produce. A `return` in the same function
  without a commit is not a dual-write bug.
- Outbox means: `INSERT` domain row and outbox row in one transaction;
  a poller reads unpublished outbox rows and produces to Kafka; a mark
  (sent / sent_at) is updated after a successful produce. Kafka
  transactions alone do not satisfy this task.

## Work to complete

1. Implement the dual-write path: open a DB transaction, insert a domain
   row (for example an `orders` row with a stable `order_id`), commit,
   then produce `{order_id, ...}` to a Kafka topic. Add a fault hook that
   kills the process after commit and before produce.
2. Run that hook. Show `SELECT` of the row succeeding and a consume of
   the topic (from earliest) missing that `order_id`. Name the kill point
   in the log.
3. Add an `outbox` table. Change the write path so the domain row and the
   outbox row commit together. Write a poller that publishes pending rows
   and marks them sent. Instrument poller restarts: kill the service
   after commit (same point as step 2) and let the poller recover.
4. Make the consumer idempotent on `order_id` (or an event id). Run a
   duplicate produce on purpose and show the domain effect happens once
   (a side-effect table with a unique constraint is a good proof).
5. Emit OpenTelemetry traces:
   - dual-write: a span for the DB write and a missing or error span for
     publish, tied by `order_id`
   - outbox: spans for commit, poll, publish, and consume, same
     `order_id` / trace or linked traces
   Export JSON or a collector dump, not only a GUI screenshot.
6. Write a `README.md` that states the transaction boundary, the
   idempotency key, and an explicit sentence that this is at-least-once
   delivery plus an idempotent consumer — not broker exactly-once.

## Evidence you'll submit

- Git history: dual-write before outbox.
- Captured dual-write loss (row yes, event no).
- Captured outbox recovery (row yes, event yes, effect once).
- Two exported traces as specified.
- `README.md` and reflection notes.

## Acceptance criteria

- [ ] The dual-write reproduction leaves a committed PostgreSQL row whose
      event never appears in a consume of the target topic after the
      named crash.
- [ ] The outbox reproduction uses one database transaction for the
      domain row and the outbox row; after the same crash and a poller
      restart, the event is consumed exactly once as a domain effect
      (duplicates allowed on the wire if the consumer is idempotent).
- [ ] Two traces (or exported spans) are submitted: one ends after the
      DB write with no publish span; one includes commit, outbox poll,
      publish, and consumer handling for the same business id.
- [ ] README names the idempotency key the consumer uses and states that
      the pipeline is at-least-once plus idempotence, not broker
      exactly-once.

## Reflection

Answer in your own words after doing the work:

1. Where, exactly, did the dual-write path lose the event — after the
   Postgres commit record was durable, or before? How do you know?
2. If the poller produces successfully and crashes before marking the
   outbox row sent, what happens? Did you test it? What did the
   consumer do?

Also record: what took longer than expected, and what remains unclear
about the gap between "the write is in Postgres" and "a consumer has
applied it."

## Mentor review guide

If a mentor reviews this work, have the apprentice replay the kill after
commit and show the outbox row still `pending`. Ask why a Kafka
transaction from the same process would still not have saved a crash
*before* the produce call. Do not approve a saga diagram without the
lost-event run.

Suggested review outcome: **Approve**, **Request revision**, or **Create
follow-up challenge**.

## AI use policy

Mode: **guided**. Explain, hint, and quiz are available; solution
generation is not. Disclose any material AI use with provider/model,
purpose, and verification performed.

## Completion gate

This task is complete only after the evidence is submitted and, when a
mentor is present, the mentor approves the demonstrated competency.
