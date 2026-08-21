# Asynchronous Work with RabbitMQ

**Task ID:** `be1t2-004`
**Estimated effort:** 16 hours
**Module:** Messaging

## Why this task exists

Some work this service does should not sit on the HTTP request. A
notification, an audit document, or a projection into MongoDB can happen
after the write is committed. This task adds RabbitMQ, a publisher in
the API process, and a consumer in a *separate* process, so the
asynchronous boundary is real rather than a function call you labelled
"async."

## Authoritative resources

- **RabbitMQ Tutorials** (reference): https://www.rabbitmq.com/tutorials
- **Python 3 Tutorial** (reference): https://docs.python.org/3/tutorial/

Start with the official tutorials for publish, consume, acknowledgements,
and dead-lettering. Implement against this service's domain — do not
submit the tutorial's "hello world" queue as the evidence.

## Work to complete

1. Add RabbitMQ to docker-compose so a clean checkout starts the API,
   PostgreSQL, MongoDB (from the previous task), and the broker.
2. On a successful domain write (for example creating the main entity),
   publish a message that names the event, the resource id, and enough
   data for a consumer to do work without guessing.
3. Run a consumer as a separate Python process (a second compose
   service is ideal). The consumer should perform a visible side effect —
   writing an audit document, updating a projection, or appending to a
   committed log file.
4. Acknowledge only after the side effect succeeds. Write down, while
   you implement this, how a duplicate delivery is handled
   (idempotent consumer or an explicit dedupe key).
5. Crash the consumer after a publish and before ack. Restart it. Show
   that the message is handled. That is at-least-once, not a hope.
6. Send one unprocessable message (bad payload or a forced handler
   exception). Dead-letter it or record the failure. Do not leave it
   retrying in a tight loop with no evidence.
7. Confirm the HTTP response is returned before the consumer finishes.
   Timestamps in the logs are the proof.

Commit compose, publisher, consumer, and the failure-path work as
separate steps. The ack/nack note should appear in history before the
final polish commit.

## Required evidence

- The compose file and the publisher/consumer Python modules, committed
  incrementally
- A log excerpt with timestamps showing the HTTP response returning
  before the consumer finishes the side effect
- A log or management-UI export showing an unacked message surviving a
  consumer crash and being handled after restart
- A demonstration of a poison or unprocessable message being
  dead-lettered or recorded, not retried in a tight loop
- A Markdown note, written while implementing ack/nack, stating how
  duplicates are handled

Submit a repository URL plus a commit reference. Do not submit only a
screenshot of the RabbitMQ management UI.

## Acceptance criteria

- [ ] A successful domain write publishes a message that a separate
      consumer process handles.
- [ ] Logs or a capture show the HTTP response timestamp earlier than
      the consumer's completion timestamp for the same write.
- [ ] Killing the consumer after publish and before ack leaves the
      message available; after restart the consumer handles it (shown
      in a log).
- [ ] An unprocessable message is routed to a dead-letter queue or a
      recorded failure, not retried indefinitely without evidence.

The mentor may kill the consumer live during review and ask you to show
the message still being processed after restart.

## Reflection

Answer these in your own words after doing the work:

1. What does at-least-once mean for *this* side effect if the consumer
   runs twice?
2. What happens to the HTTP caller if the broker is down at publish
   time — and is that the behavior you want?
3. Why is a function call in the same process not a substitute for
   this queue?

Also record:

- What took longer than expected?
- What would you change about the message schema next time?
- What remains unclear?

## Mentor review guide

- Confirm the consumer is a separate process or compose service, not a
  background thread started inside the request handler.
- Ask to see the crash-before-ack demonstration, not a description of
  it.
- Reject a submission that acks before the side effect or that has no
  poison-message path.

Suggested review outcome: **Approve**, **Request revision**, or **Create
follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes.
Solution generation is not the intended path for this task. Material AI
assistance must be disclosed with the provider/model (if known), purpose,
and verification performed.

## Completion gate

This task is complete only once the evidence is submitted and the mentor
approves the demonstrated delivery behavior — not when a message appears
once in the management UI.
