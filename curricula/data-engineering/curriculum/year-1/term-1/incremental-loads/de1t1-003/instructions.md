# Incremental Loads with a Watermark You Can Defend

**Task ID:** `de1t1-003`
**Estimated effort:** 8 hours
**Module:** Incremental Loads

## Why this task exists

A full refresh every run will not survive volume. Incremental loads need a
cursor you can explain: what it stores, when it advances, and what happens to
a row whose timestamp is behind that cursor.

If the watermark moves before the warehouse commit, the next run skips work
that never landed. That bug looks like "the source had no data."

## Authoritative resources

- **Python 3 Tutorial** (reference): https://docs.python.org/3/tutorial/
- **PostgreSQL Documentation** (reference): https://www.postgresql.org/docs/current/
  — transactions, `MAX`, and a small state table are the relevant pieces.

Use official documentation as the primary source. If you use anything else,
record it in your notes.

## Work to complete

1. Add a watermark store (a PostgreSQL table or a file the job owns). It
   records the last source timestamp or monotonic id that was successfully
   committed to the warehouse.
2. Change the extract so a normal run pulls only rows strictly after the
   stored watermark (or after watermark minus a documented lookback, if that
   is your late-row policy).
3. Advance the watermark only after the warehouse write commits. Put the
   write and the watermark update in an order you can defend — one
   transaction if both live in PostgreSQL.
4. Inject five late rows whose timestamps sit behind the current watermark.
   Write a policy: lookback window, late table/file, or reject log. Apply it.
   Each of the five must appear in exactly one of those places.
5. Kill the job after extract (or after a warehouse write you then roll
   back) but before the watermark is updated. Rerun. The uncommitted batch
   must still load.

## Required evidence

- The watermark store and the code that reads and writes it
- Captured watermark values and warehouse counts before and after a
  successful incremental run
- A captured incremental run against a source that contains only older
  rows, showing zero new warehouse rows
- A late-row policy note plus the fate of the five injected rows
- A crash-before-watermark-update demonstration with the following rerun's
  captured keys
- Reflection notes answering the questions below

Submit a repository URL plus a commit reference. Do not submit only a
description of what you would have done.

## Acceptance criteria

- [ ] After a successful incremental run, the stored watermark equals the
      maximum source timestamp or id of rows actually committed to the
      warehouse, shown by a query or file dump.
- [ ] An incremental run against a source that contains only rows at or
      behind the watermark loads zero new warehouse rows, with captured
      counts.
- [ ] A written late-row policy is demonstrated on five injected rows, and
      each of those five appears in exactly one of: a lookback load, a late
      table or file, or a reject log.
- [ ] A run that is killed after extract but before the watermark update,
      then rerun, still loads the uncommitted batch (captured keys include
      that batch).

The mentor may change the watermark by hand to an earlier value and ask you
what the next run will do. If you cannot predict the key set, the store is
not yet a control surface.

## Reflection

Answer these in your own words after doing the work:

1. Why must the watermark not advance inside the extract, before the
   warehouse commit?
2. Which of lookback, late table, or reject did you choose, and what
   consumer question becomes unanswerable under that choice?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you learned the objective?

## Mentor review guide

Ask the apprentice to point at the exact line that writes the watermark and
the exact line that commits warehouse rows, and to say what happens if the
process dies between them. Do not approve a watermark stored only in memory.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not
the intended path for this task. The apprentice must be able to explain and
rerun the crash demonstration. Material AI assistance must be recorded in the
submission notes with the provider/model (if known), purpose, and verification
performed.

## Completion gate

This task is not complete when incremental mode "works on happy data." It is
complete once the watermark, late-row, and crash-before-update evidence is
submitted and the mentor approves the demonstrated competency.
