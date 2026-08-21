# Recover a Failed Production Load From Evidence

**Task ID:** `de1t3-002`
**Estimated effort:** 10 hours
**Module:** Failure Recovery

## Why this task exists

You have jobs, a DAG, a stream, and a warehouse. Something will fail in
a way the happy-path tests did not name. The skill is not "run it
again." The skill is: build a timeline from artifacts, restore last-good
from a snapshot you can show, replay a bounded window, and say what
would have paged.

If mentorship is optional for you, write the incident note as if a
peer will pick it up cold. If you have a mentor, they will ask you to
defend every timeline line.

## Authoritative resources

- **Apache Kafka Documentation** (reference): https://kafka.apache.org/documentation/
  — offsets, consumer groups, replay.
- **PostgreSQL Documentation** (reference): https://www.postgresql.org/docs/current/
  — counts, checksums, rollbacks, restoring a table from a copy.
- **Apache Airflow Documentation** (reference): https://airflow.apache.org/docs/apache-airflow/stable/
  — task states and clearing a run versus inventing a new one.

Use official documentation as the primary source. If you use anything else,
record it in your notes.

## Work to complete

1. Start from the running system you already built (a reduced fixture
   is fine if it still has a batch path or a stream path, logs, and a
   warehouse). Capture a pre-incident snapshot or checksum of the
   consumer-facing table (row count plus a hash of keys, or a table
   copy).
2. Inject one real failure, not a comment: a poison payload, a stopped
   broker, a unique-constraint storm, or a permission failure that
   simulates a full disk. Let the job or consumer fail in public.
3. Diagnose using only logs, metrics, offsets or watermarks, scheduler
   states, and warehouse queries. Write a timeline with at least three
   timestamped entries. Each entry cites an artifact — a log line, a
   metric value, an offset, a query result. Recollection does not
   count.
4. Restore last-good so the consumer-facing data matches the
   pre-incident snapshot or checksum. No guess-deletes of "probably
   Tuesday."
5. Replay or reprocess the failed window. Expected counts, no
   duplicate natural keys or `event_id`s. In the note, name the
   detection signal that would have paged — or name the gap that would
   have left this silent.

## Required evidence

- An incident note with a timestamped timeline of at least three
  entries that each cite a log line, metric, offset or watermark, or
  query result
- A captured pre-incident snapshot or checksum and a post-restore query
  that matches it
- Post-replay window counts and a uniqueness check on the natural key
  or `event_id`
- The detection-signal paragraph
- Reflection notes answering the questions below

Submit a repository URL plus a commit reference for any recovery
tooling. The incident note is part of the submission, not a sidebar.

## Acceptance criteria

- [ ] The incident note contains a timestamped timeline with at least
      three entries that each cite a log line, metric, offset or
      watermark, or query result — not recollection.
- [ ] Last-good restore is demonstrated by a query showing
      consumer-facing data matching a captured pre-incident snapshot or
      checksum.
- [ ] Replay after restore produces the expected window counts without
      duplicate natural keys or `event_id`s.
- [ ] The note names the detection signal that would have paged, or
      states why this failure would have been silent, with the signal
      or gap named specifically.

The mentor may withhold the failure type and ask you to diagnose from
the artifacts only. If the first step is "I restarted everything,"
request revision.

## Reflection

Answer these in your own words after doing the work:

1. Which timeline line changed what you did next, and what would you
   have done wrongly without it?
2. What is still not observable that a next incident would need?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you learned the objective?

## Mentor review guide

Ask the apprentice to recover while you watch, using only the artifacts
in the note. Do not approve a restore that cannot be checked against the
pre-incident checksum. Blame-free language; name systems, not people.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is
not the intended path for this task. The apprentice must be able to walk
the timeline aloud. Material AI assistance must be recorded in the
submission notes with the provider/model (if known), purpose, and
verification performed.

## Completion gate

This task is not complete when the system is green again. It is complete
once the cited timeline, the checksum-matched restore, the clean replay,
and the paging-signal paragraph are submitted and the mentor approves
the demonstrated competency.
