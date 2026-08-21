# Tune a Query From the Plan, Not a Folklore Index

**Task ID:** `pe1t1-005`
**Estimated effort:** 12 hours
**Module:** Database tuning

## Why this task exists

`y1t2-003` asks for EXPLAIN before and after an index. This task goes further:
the dataset must be large enough that the planner has a real choice, you quote
**actual time** and **buffers**, and you keep a paper trail for an index that
did **not** pay for itself. Folklore ("always index foreign keys," "never
sequential scan") is not evidence.

## Authoritative resources

- **PostgreSQL Documentation** (primary): https://www.postgresql.org/docs/current/
  — `EXPLAIN`, `EXPLAIN ANALYZE`, `BUFFERS`, index types, and `pg_stat`
  views as needed. Use the current-version docs, not a random blog's plan
  snippet.

## Work to complete

1. Load a PostgreSQL database with **at least 100,000 rows** in the table the
   query hits (or get a written mentor exception if your environment cannot;
   the exception must say why a smaller set still changes Seq Scan vs Index
   Scan). Record the row count from `COUNT(*)` or `pg_class`, not from memory.
2. Write one realistic query the application would run (filter + join or
   filter + sort/aggregate — not `SELECT * FROM t LIMIT 1`).
3. Run `EXPLAIN (ANALYZE, BUFFERS)` **before** adding or changing indexes.
   Commit the full text. Quote **actual total time** and at least one buffer
   number (`shared hits` or `shared reads`).
4. Add an index you believe will help. Re-run the same `EXPLAIN (ANALYZE,
   BUFFERS)`. Keep this index only if actual time dropped. Quote both times.
5. Add a **second** index (or a different column/order) that looks plausible.
   Measure it. If actual time does not improve by at least 20% — or gets
   worse — document both times and do **not** recommend that index as the
   default. Drop it or leave it disabled in the recommended schema.
6. In your own words, interpret the before plan's node that dominated actual
   time (Seq Scan, Nested Loop, Sort, …) and what changed after the kept
   index.

## Required evidence

- Row-count note (≥ 100,000 or mentor exception)
- Before `EXPLAIN ANALYZE` text with actual time and a buffer statistic
- After `EXPLAIN ANALYZE` text for the kept index
- Second-index plan pair showing < 20% gain or a regression
- Reflection notes

Do not submit only screenshots of a GUI. The plan text must be copy-pasteable.

## Acceptance criteria

- [ ] The dataset note states a row count of at least 100,000, or a
      mentor-written exception naming why a smaller set still changes the
      plan.
- [ ] Before and after `EXPLAIN ANALYZE` outputs are committed as text and
      each quotes actual total time plus shared hits or shared reads.
- [ ] The kept index is the one whose after actual time is lower than the
      before actual time; both times are quoted from the plans.
- [ ] A second index is documented with before/after actual times showing
      less than 20% improvement or a regression, and it is not the
      recommended default.

The mentor may hand you a new `WHERE` clause and ask for a live `EXPLAIN`.
"It uses an index" without actual time is not a pass.

## Reflection

Answer these in your own words after doing the work:

1. Why can a plan that uses an index still be slower than a sequential scan
   on this dataset? Quote a number from one of your plans.
2. What write-path cost did the kept index add, and did you measure it
   (even roughly, as insert time or `pg_stat` write figures)?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Change the query predicate and ask for a new `EXPLAIN ANALYZE` live.
- Ask why the rejected index looked plausible before the numbers.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may explain `EXPLAIN` fields and quiz you on node types. It must not invent
plan timings. Disclose material AI assistance with provider/model, purpose,
and verification performed.

## Completion gate

Complete only after both plans, the rejected index numbers, and the row count
are submitted and the mentor approves the interpretation.
