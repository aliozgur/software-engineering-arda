# Fail Closed When a Batch Violates Quality

**Task ID:** `de1t1-006`
**Estimated effort:** 8 hours
**Module:** Quality Gates

## Why this task exists

This is not exploratory missingness analysis. It is a gate: after staging,
before consumers can see the new batch, checks run. If they fail, the
consumer-facing table stays at last-good. The reject is stored with a
reason. The run is identifiable in the logs.

A warehouse that is "mostly right" after a bad file is harder to repair
than a warehouse that refused the file.

## Authoritative resources

- **pandas User Guide** (reference): https://pandas.pydata.org/docs/user_guide/index.html
  — use it for check calculations if you want; SQL checks are equally valid.
- **PostgreSQL Documentation** (reference): https://www.postgresql.org/docs/current/
  — transactions, swap/rename patterns, and quarantine tables.

Use official documentation as the primary source. If you use anything else,
record it in your notes.

## Work to complete

1. Add quality checks that run after staging and before publish. Cover at
   least: freshness (source or staging max time versus now, with a
   threshold), a volume band (row count versus a documented min/max or
   versus the previous run), and one content check (null rate on a
   required field, or values outside an allowed set).
2. Publish to the consumer-facing warehouse table only if every check
   passes. Use a transaction, a swap of a shadow table, or an equivalent
   mechanism so a failed gate cannot leave a half-written consumer table.
3. Inject a bad batch that fails exactly one named check. Capture
   consumer-table row count or `max(updated_at)` before and after.
4. Write rejected rows or the rejected batch id to a quarantine table or
   file with a reason. Emit a structured log line that includes `run_id`,
   check name, and pass/fail.
5. Run a good batch after the failure. It must publish. Last-good plus one
   successful publish is the story, not "we deleted everything and started
   over" unless that is the documented full-refresh path and you still
   show the failed batch never became consumer-visible.

## Required evidence

- The check definitions in code or config
- Before and after queries on the consumer-facing table around a failing
  batch
- A structured log line for the failed check that includes `run_id` and
  check name
- The quarantine table or file showing rejected rows or the rejected batch
  id with a reason
- Captured counts proving a later good batch published after the failure
- Reflection notes answering the questions below

Submit a repository URL plus a commit reference. Include the log line as
text, not only a screenshot of a terminal theme.

## Acceptance criteria

- [ ] A batch that fails a named check leaves the consumer-facing
      warehouse table's row count or `max(updated_at)` unchanged, shown by
      captured before and after queries.
- [ ] The failing check name and a `run_id` appear in a structured log
      line that parses as JSON or a documented key=value format.
- [ ] Rejected rows or the rejected batch id appear in a quarantine table
      or file with a reason column or field populated.
- [ ] A subsequent good batch publishes successfully after the failed one,
      shown by captured counts that change only on the good run.

The mentor may hand you a batch that fails a different check than the one
you demoed. The same publish path must refuse it. Do not approve a gate
that only `print`s a warning and still writes.

## Reflection

Answer these in your own words after doing the work:

1. What would a consumer have queried during the failed run, and how do
   you know they did not see the bad batch?
2. When would you fail the whole batch versus quarantining individual
   rows, and which did you implement?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you learned the objective?

## Mentor review guide

Ask the apprentice to show the transaction or swap that keeps last-good
visible. If publish is "insert then hope the check runs," request
revision. Prefer a live failed batch over a verbal description.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is
not the intended path for this task. The apprentice must be able to
explain why last-good stayed queryable. Material AI assistance must be
recorded in the submission notes with the provider/model (if known),
purpose, and verification performed.

## Completion gate

This task is not complete when checks exist. It is complete once the
failed-batch last-good evidence, the quarantine, the log line, and the
following good publish are submitted and the mentor approves the
demonstrated competency.
