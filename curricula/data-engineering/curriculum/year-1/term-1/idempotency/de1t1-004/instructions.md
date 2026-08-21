# Crash the Job Mid-Load and Recover Without Duplicates

**Task ID:** `de1t1-004`
**Estimated effort:** 8 hours
**Module:** Idempotency

## Why this task exists

Pipelines fail in the middle. The next operator action is almost always "run
it again." If that second run inserts a second copy of the same natural key,
you have not built a pipeline — you have built a landmine.

Idempotency here means: the same job command, pointed at the same source
window, leaves the warehouse in the same key set whether it ran once or
three times, including after a crash.

## Authoritative resources

- **Python 3 Tutorial** (reference): https://docs.python.org/3/tutorial/
- **PostgreSQL Documentation** (reference): https://www.postgresql.org/docs/current/
  — `INSERT ... ON CONFLICT`, `MERGE`, unique constraints, and transactions.

Use official documentation as the primary source. If you use anything else,
record it in your notes.

## Work to complete

1. Implement the warehouse write as an upsert (`INSERT ... ON CONFLICT` /
   `MERGE`) or a delete-insert keyed by a documented natural key. A
   surrogate identity column is not the natural key.
2. Add an automated test that fails if any natural key appears more than
   once in the target. Prove the test can fail: commit a fixture that
   introduces a duplicate and capture that failing run, then restore the
   happy fixture.
3. Crash the job mid-load — raise after N rows, or kill the process after
   staging is written and a partial warehouse write has started. Restart
   with the same command. Uniqueness must hold and the expected key set
   must match the source snapshot.
4. After a fully successful load, run the same command again. Warehouse
   row count must change by zero.
5. Do not add a one-off "dedupe.sql" that you only run for the demo. Retry
   uses the same entrypoint as the happy path.

## Required evidence

- The upsert or delete-insert load path and the natural key it uses
- A test run that fails when a duplicate natural key is inserted, plus the
  commit that introduced the duplicate fixture
- Captured warehouse key counts after a mid-load crash and restart
- Captured warehouse row count before and after retrying an
  already-successful load
- Reflection notes answering the questions below

Submit a repository URL plus a commit reference. Include the failing-test
capture; a passing suite alone is not enough.

## Acceptance criteria

- [ ] A named automated test fails when a duplicate natural key is
      inserted, shown by a commit that introduces a duplicate fixture and a
      captured failing test run.
- [ ] After a mid-load crash and a restart of the same job command, the
      warehouse has no duplicate natural keys and matches the source
      snapshot's expected key set.
- [ ] Retrying an already-successful load changes the warehouse row count
      by zero, shown as before and after counts.
- [ ] The warehouse write used on retry is the same function or job
      entrypoint as the happy path, not a separate cleanup script that
      exists only for the demonstration.

The mentor may crash the job themselves and ask you to recover while they
watch. If recovery needs a handwritten `DELETE`, the write path is not
idempotent yet.

## Reflection

Answer these in your own words after doing the work:

1. What is the natural key, and what would break if you had used only a
   surrogate `id`?
2. If two overlapping incremental windows both contain the same natural
   key with different payloads, which version wins, and where is that
   rule written?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you learned the objective?

## Mentor review guide

Ask the apprentice to point at the unique constraint and the write
statement and to explain what happens on a second insert of the same key.
Do not approve "we truncate the table before every retry" unless that is
the documented full-refresh strategy and they can say what incremental
mode would do.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is
not the intended path for this task. The apprentice must be able to
reproduce the crash and the failing test without the model in the room.
Material AI assistance must be recorded in the submission notes with the
provider/model (if known), purpose, and verification performed.

## Completion gate

This task is not complete when the happy-path load is unique. It is
complete once the failing test, the crash restart, and the zero-delta
retry are submitted and the mentor approves the demonstrated competency.
