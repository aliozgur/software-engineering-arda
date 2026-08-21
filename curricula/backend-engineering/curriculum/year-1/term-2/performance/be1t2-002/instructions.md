# Index and Explain the Slow Queries

**Task ID:** `be1t2-002`
**Estimated effort:** 14 hours
**Module:** Performance

## Why this task exists

The schema from Term 1 is correct enough to store data. It has not been
asked to stay fast under a realistic access pattern. This task forces you
to measure the queries the API already runs, change only what the plans
justify, and keep the measurement so a mentor can reopen it.

## Authoritative resources

- **PostgreSQL Documentation** (reference): https://www.postgresql.org/docs/current/

Use the chapters on `EXPLAIN`, indexes, and statistics. Prefer the
official docs over blog posts that recommend indexing every foreign key
by default.

## Work to complete

1. List at least three queries the running API actually issues — taken
   from the code or from a query log, not invented for the exercise.
2. Load enough sample data that a sequential scan is visible (hundreds
   of rows is usually enough; thousands is better). Record the row
   counts you used.
3. Run `EXPLAIN ANALYZE` on each query *before* adding indexes. Commit
   those plans as files.
4. Add only the indexes those plans justify. Write them as a migration
   in the existing sequence, not as a hand-run `CREATE INDEX`.
5. Re-run `EXPLAIN ANALYZE` on the same queries with the same data.
   Commit the after plans.
6. Leave at least one of the three queries without a new index and write
   down why — while you are deciding, not after the fact.
7. Update the README with a table: query, before plan type and time,
   after plan type and time, index used (or "none").

Do not add an index first and then go looking for a plan that flatters
it. The measurement commits should land before the migration commit.

## Required evidence

- Committed before and after `EXPLAIN ANALYZE` plans for at least three
  API-backed queries, as files, not paraphrases
- The migration that adds the justified indexes, in the existing
  migration sequence
- A README table listing each query, before plan type and time, after
  plan type and time, and the index used
- A short note, written when you decided not to index one query,
  explaining why
- Git history showing measurement commits before the index migration,
  not the other way around

Submit a repository URL plus a commit reference. Do not submit only
screenshots of the query planner GUI.

## Acceptance criteria

- [ ] At least one committed pair of plans shows a Seq Scan becoming an
      Index Scan or Index Only Scan after the migration.
- [ ] Before and after plans are files in the repository, each produced
      by `EXPLAIN ANALYZE`, not reconstructed from memory.
- [ ] A query that was not indexed is documented in the repository with
      a written reason.
- [ ] The index migration applies on an empty database after the
      existing Term 1 migrations, with no hand-run SQL.

The mentor may pick one query, drop the index live, and ask you to show
the plan regressing.

## Reflection

Answer these in your own words after doing the work:

1. Which plan node actually changed, and what does that node mean?
2. What would an index on the unindexed query have cost you on writes?
3. How would you notice this regression if someone later dropped the
   index?

Also record:

- What took longer than expected?
- What would you measure again before adding another index?
- What remains unclear?

## Mentor review guide

- Open the before/after plan files and confirm they are real
  `EXPLAIN ANALYZE` output, not rewritten summaries.
- Ask which statistic (row estimate vs actual) surprised the apprentice.
- Reject a submission that indexes every foreign key with no plan
  showing a sequential scan.

Suggested review outcome: **Approve**, **Request revision**, or **Create
follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes.
Solution generation is not the intended path for this task. Material AI
assistance must be disclosed with the provider/model (if known), purpose,
and verification performed.

## Completion gate

This task is complete only once the evidence is submitted and the mentor
approves the demonstrated measurement — not when an index merely exists
on a column.
