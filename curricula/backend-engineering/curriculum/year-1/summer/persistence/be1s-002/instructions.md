# Integrate Relational, Document and Queue Persistence

**Task ID:** `be1s-002`
**Estimated effort:** 18 hours
**Module:** Persistence

## Why this task exists

`be1s-001` froze the hops. This task builds them. A successful
domain write must land in PostgreSQL, publish a message, and
appear in MongoDB after the consumer runs — and the broker-down
case must do what the design said it would do, not whatever the
library default is.

## Authoritative resources

- **PostgreSQL Documentation** (reference): https://www.postgresql.org/docs/current/
- **MongoDB Manual** (reference): https://www.mongodb.com/docs/manual/
- **RabbitMQ Tutorials** (reference): https://www.rabbitmq.com/tutorials

Use each manual for the hop it owns. Do not invent a fourth
store.

## Work to complete

Implement the write path from the approved design. If the design
has to change, update `be1s-001` artifacts in the same pull
request and say so in the evidence note.

1. Keep the domain invariants in a PostgreSQL transaction. The
   HTTP success for the *sync* part of the write means the
   relational commit succeeded.
2. Publish the event the design named. Prefer publishing after
   commit, or use an outbox table if you chose that in the
   design — do not publish inside a transaction you then roll
   back without a documented recovery.
3. Consumer projects the event into MongoDB (audit, view, or
   the document shape you chose in Term 2). The document key
   must match the relational id so a mentor can follow one
   write across stores.
4. Stop RabbitMQ and perform the write. Do the thing the design
   promised: a documented 5xx/503, or an outbox row that a
   later process can drain. Capture it.
5. Automate the happy path and the broker-down path as
   integration tests that reset store state between runs.
6. Compose must start API, PostgreSQL, MongoDB and RabbitMQ.
   The consumer may be a second service in the same compose
   file.

Commit in the order of the hops: transaction, publish, consumer,
broker-down. A single "integrate everything" commit hides the
work.

## Required evidence

- Git history showing the transaction, the publish, the consumer
  projection, and the broker-down path as separate commits
- A demonstration that one write is visible in PostgreSQL and,
  after consume, in MongoDB, with ids that match the data-flow
  note
- A demonstration of the documented broker-down behavior
  (5xx/503 or an outbox row), with the compose/broker stopped
- Integration-test output covering the happy path and the
  broker-down path
- The compose file that starts the API, PostgreSQL, MongoDB and
  RabbitMQ together

Submit a repository URL plus a commit reference. Do not submit
only screenshots of three GUIs.

## Acceptance criteria

- [ ] A single domain write is present in PostgreSQL and, after
      the consumer runs, present in MongoDB with a key that
      matches the relational id.
- [ ] With RabbitMQ stopped, the API either returns a documented
      5xx/503 or records an outbox row — the chosen behavior is
      shown, not described.
- [ ] An integration test covers the happy path and the
      broker-down path and is part of the committed suite.
- [ ] `docker compose up` starts the API, PostgreSQL, MongoDB
      and RabbitMQ from the committed compose file.

The mentor may stop the broker live and ask you to show the
designed behavior, then start it and drain any outbox.

## Reflection

Answer these in your own words after doing the work:

1. Where can a write be in Postgres but not in MongoDB, and for
   how long is that acceptable?
2. What did you change from the `be1s-001` design once the
   code existed?
3. What would a second consumer on the same queue do to your
   documents?

Also record:

- What took longer than expected?
- What would you make synchronous if you started over?
- What remains unclear?

## Mentor review guide

- Follow one write id from the HTTP response to Postgres to the
  queue payload to MongoDB.
- Stop the broker and confirm the designed behavior, not an
  unhandled exception.
- Reject a consumer running inside the request handler, and a
  publish that can succeed after a rolled-back transaction
  with no outbox.

Suggested review outcome: **Approve**, **Request revision**, or
**Create follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and
quizzes. Solution generation is not the intended path for this
task. Material AI assistance must be disclosed with the
provider/model (if known), purpose, and verification performed.

## Completion gate

This task is complete only once the evidence is submitted and
the mentor approves the demonstrated path — not when all three
systems merely start.
