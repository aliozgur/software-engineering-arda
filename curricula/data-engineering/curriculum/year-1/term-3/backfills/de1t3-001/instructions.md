# Backfill a Historical Window Without Rewriting the Present

**Task ID:** `de1t3-001`
**Estimated effort:** 10 hours
**Module:** Backfills

## Why this task exists

You will need to reprocess. A bug in a transform, a late source dump, a
contract that started being enforced last Tuesday — all of those ask for
a bounded replay. If the backfill job is a fork of the incremental job,
they will drift. If it has no date bounds, it will rewrite today.

Partition the warehouse. Keep today's incremental job running. Backfill
a closed window with the same transform. Prove today did not move.

## Authoritative resources

- **Apache Airflow Documentation** (primary): https://airflow.apache.org/docs/apache-airflow/stable/
  — backfill, logical dates, catching up a DAG without inventing a
  second codebase. A CLI or Makefile wrapper with start/end is
  acceptable if it calls the same callable the DAG would.
- **PostgreSQL Documentation** (reference): https://www.postgresql.org/docs/current/
  — table partitioning, or a date column you treat as a partition key
  with queries that always filter it.

Use official documentation as the primary source. If you use anything else,
record it in your notes.

## Work to complete

1. Partition the consumer-facing warehouse by day (or hour). If native
   partitioning is more than you want, a required `ds` / `window_start`
   column that every publish and every query filters is the minimum —
   write that convention down.
2. Keep the incremental job running for the current window ("today" in
   the fixture clock is fine).
3. Run a backfill for a closed window of at least three days (or three
   hours if you partitioned by hour). The backfill command or DAG takes
   explicit start and end parameters. It must not scan "all history."
4. Incremental and backfill must call the same transform function or
   module, parameterized by window. No copied file with a tweak.
5. Capture row count and `max(updated_at)` (or equivalent) on the
   current partition before and after the backfill. They must match.
   Re-run the same backfill window. That window's row count must change
   by zero. Log a `run_id` or Airflow run id for the backfill.

## Required evidence

- The backfill command or DAG parameters that take an explicit start
  and end date
- Before and after queries of the current (non-backfill) partition's
  row count and `max(updated_at)`
- Before and after row counts for the backfilled window, including a
  second run that changes the count by zero
- The shared transform function or module imported by both paths
- A `run_id` or Airflow run identifier for the backfill, captured in
  logs
- Reflection notes answering the questions below

Submit a repository URL plus a commit reference.

## Acceptance criteria

- [ ] The backfill command or DAG takes an explicit start and end date
      and does not scan all history, shown in code or DAG parameters.
- [ ] Row count and `max(updated_at)` of the current non-backfill
      partition are identical before and after the backfill, shown by
      captured queries.
- [ ] Re-running the same backfill window changes that window's row
      count by zero.
- [ ] Backfill and incremental invoke the same transform function or
      module, parameterized by window, shown by import or task
      callable.

The mentor may ask you to backfill a window that overlaps "today" and
refuse if your command allows it without an extra flag. Overlap should
be hard or loudly confirmed.

## Reflection

Answer these in your own words after doing the work:

1. What would have happened to today's partition if the backfill
   omitted the date filter, and how do you know that did not happen?
2. If the transform changes again next month, what stops a future
   backfill from applying two different logics to adjacent days?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you learned the objective?

## Mentor review guide

Ask the apprentice to show the single transform callable and the two
callers. If backfill is `load_all.sql` and incremental is Python, request
revision. Prefer a live second backfill over a claim of idempotency.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is
not the intended path for this task. The apprentice must be able to
predict today's counts before rerunning. Material AI assistance must be
recorded in the submission notes with the provider/model (if known),
purpose, and verification performed.

## Completion gate

This task is not complete when history is reloaded. It is complete once
the bounded command, the unchanged current partition, the zero-delta
rerun, and the shared transform are submitted and the mentor approves
the demonstrated competency.
