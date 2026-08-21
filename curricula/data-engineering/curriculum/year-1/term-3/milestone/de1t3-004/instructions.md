# Ship a Production-Shaped Pipeline and Break It On Purpose

**Task ID:** `de1t3-004`
**Estimated effort:** 12 hours
**Module:** Milestone

## Why this task exists

The earlier tasks built pieces. This one asks you to run them as one
system: a batch path and a stream path, contracts on the way in, a DAG
that sequences the batch side, tests you still trust after a failure,
one bounded backfill you can point at, and enough instrumentation to
recover from evidence.

This is not a new product idea and not an analytics showcase. It is
pipeline engineering under a live break.

If you work without a mentor, pick the failure yourself and write the
note as if a peer will review it. If you have a mentor, they pick the
failure.

## Authoritative resources

- **PostgreSQL Documentation** (reference): https://www.postgresql.org/docs/current/
- **Apache Kafka Documentation** (reference): https://kafka.apache.org/documentation/
- **RabbitMQ Tutorials** (reference): https://www.rabbitmq.com/tutorials
- **Apache Airflow Documentation** (reference): https://airflow.apache.org/docs/apache-airflow/stable/
- **Python 3 Tutorial** (reference): https://docs.python.org/3/tutorial/

Use the same official sources as earlier tasks. Record anything else.

## Work to complete

1. Assemble (or keep assembling) one repository that can: extract and
   load a batch window, consume a stream, validate against a contract,
   run a DAG for the batch path, run a test command, and backfill one
   closed window. Document the command for each.
2. Land both inbound paths in a documented shared warehouse table, or
   in two tables joined by a documented key. Capture a query that
   returns rows originating from both sources.
3. Confirm instrumentation from `de1t3-003` still answers freshness and
   volume on this combined system — even if you only emit a subset
   during the break.
4. Inject one failure, chosen by the mentor when present, otherwise by
   you from this list: a contract-breaking payload, a late burst that
   hits the lateness policy, a DAG task failure, or a poison stream
   event. Recover. Capture before/after counts and a short
   incident/recovery note.
5. Run the documented test command after recovery. It must pass. Git
   history for this work must be more than one commit.
6. Write a short architecture note: one decision you would not repeat,
   with the failure that taught it.

## Required evidence

- Documented commands that run the batch job, the stream consumer, the
  validator, the DAG, and the test suite
- A query showing warehouse rows from both sources, with the join or
  shared key documented
- Before and after counts plus an incident or recovery note for the
  injected failure
- A captured passing test-command run after recovery
- Git history spanning the work, not a single final commit
- Reflection notes answering the questions below

Submit a repository URL plus a commit or tag reference.

## Acceptance criteria

- [ ] The repository contains a batch job, a stream consumer, a
      contract file, a DAG, and a test command, each runnable from a
      documented command.
- [ ] Batch and stream paths write to a documented shared warehouse
      table or to two tables joined by a documented key, and a query
      shows rows originating from both sources.
- [ ] An injected failure and its recovery are captured with before and
      after counts and an incident or recovery note.
- [ ] The documented test command is run after recovery and passes.
- [ ] Git history contains more than one commit for this task's work.

The mentor may ask you to break a different piece live after you recover
the first. Passing tests that were not run after recovery do not count.

## Reflection

Answer these in your own words after doing the work:

1. Which boundary — contract, watermark, offset, or DAG state — actually
   saved you during the injected failure?
2. What would you delete from the system to make recovery easier, and
   what capability would you lose?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you learned the objective?

## Mentor review guide

Pick the failure. Watch the recovery. Ask for the both-sources query
and the post-recovery test command. Do not approve a milestone that is
only one path with a mock for the other, unless the mock is a real
consumer against a recorded log and is documented as such.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is
not the intended path for this task. The apprentice must recover and
explain without a generated runbook. Material AI assistance must be
recorded in the submission notes with the provider/model (if known),
purpose, and verification performed.

## Completion gate

This task is not complete when both paths have run once. It is complete
once the dual-source query, the injected failure and recovery, the
post-recovery passing tests, and the architecture note are submitted
and the mentor approves the demonstrated competency.
