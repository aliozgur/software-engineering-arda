# Stage Operational Data Before You Model It

**Task ID:** `de1t1-001`
**Estimated effort:** 8 hours
**Module:** Warehouse Modeling

## Why this task exists

This path is pipeline engineering, not analytics. You are not answering a business
question and you are not building a dashboard. You are deciding how operational
records will land so a later job can rerun, backfill, and recover without guessing
what the source looked like.

Staging preserves source grain. The warehouse is the contracted shape consumers
read. Mixing those two is how silent rewrites start.

## Authoritative resources

- **PostgreSQL Documentation** (primary): https://www.postgresql.org/docs/current/
  — schemas, primary keys, unique constraints, and `CREATE TABLE` are enough for
  this task. Read the sections you actually use.

Use official documentation as the primary source. If you use anything else, record
it in your notes.

## Work to complete

1. Pick one operational source with at least three entity types and a time column
   (orders and line items, tickets and comments, shipments and events — your
   choice). A small CSV or generated fixture is fine. Do not use a pre-modeled
   analytics extract as the "source."
2. Write a source-to-target map: every source field → staging column → warehouse
   column, or "dropped" with a one-line reason.
3. In PostgreSQL, create schemas named `staging` and `warehouse`. Staging tables
   keep source grain (append-oriented copies). Warehouse tables declare grain and
   primary keys. Use either one fact plus at least two dimensions, or one wide
   table whose grain is stated in a comment on the table.
4. Choose one attribute that changes over time. Write an SCD type-1 versus type-2
   decision. Include one example query that would return a wrong answer if you
   had chosen the other type.
5. Load a small sample only to prove the DDL works. This task is the model, not
   the pipeline — the next task writes the job.

## Required evidence

- A source-to-target map covering every source field
- Committed SQL DDL that creates the schemas and tables
- An SCD decision note that includes the wrong-answer query
- A captured listing of the created schemas and tables
- Reflection notes answering the questions below

Submit a repository URL plus a commit reference. Do not submit only screenshots
of the SQL editor.

## Acceptance criteria

- [ ] The source-to-target map lists every source field as either landed in a
      named staging column or explicitly dropped with a one-line reason.
- [ ] A comment or note on the warehouse fact or primary table states the grain
      in one sentence.
- [ ] One changing attribute has a written SCD type-1 versus type-2 decision plus
      one example query that returns a wrong answer under the rejected choice.
- [ ] PostgreSQL schemas named `staging` and `warehouse` exist, and a captured
      `\d` or `information_schema` listing shows at least one table in each.

The mentor may point at a warehouse column and ask whether it can be rebuilt
from staging alone. If the answer is no and that was not written down as a
drop, the map is incomplete.

## Reflection

Answer these in your own words after doing the work:

1. If staging were deleted tonight, which warehouse column could you no longer
   rebuild, and why is that column still in the warehouse?
2. What query would a later backfill run against staging that it must not run
   against the warehouse?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you learned the objective?

## Mentor review guide

Ask the apprentice to add one new source field live and say whether it lands in
staging only, staging and warehouse, or is dropped — and what a rerun would do
with historical rows. Do not approve a star schema that exists only as a
diagram with no DDL.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**. Prefer questions that force grain and rebuild reasoning over
cosmetic rename requests.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not
the intended path for this task. The apprentice must be able to explain, modify
and defend every submitted table and mapping line. Material AI assistance must
be recorded in the submission notes with the provider/model (if known), purpose,
and verification performed.

## Completion gate

This task is not complete when the tables exist. It is complete once the map,
grain statement, SCD decision, and schema listing are submitted and the mentor
approves the demonstrated competency.
