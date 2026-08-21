# Relational Schema Design for a Service Domain

**Task ID:** `be1t1-003`
**Estimated effort:** 14 hours
**Module:** Relational Data

## Why this task exists

A schema that "looks right" but has no constraints will let bad data in the
first week it's used for anything real. The next task builds a REST API
directly on top of what you design here, so the mistakes you make in this
task are the ones you will be living with two tasks from now.

## Authoritative resources

- **PostgreSQL Documentation** (reference): https://www.postgresql.org/docs/current/

Use the linked documentation as the primary source, especially the chapters
on constraints, indexes and the `EXPLAIN` command.

## Work to complete

1. Pick a small service domain (a ticketing system, an inventory tracker, a
   bookings system, or similar) with at least three related entities.
2. Design a normalized schema (3NF where reasonable) with primary/foreign
   keys and constraints (`NOT NULL`, `UNIQUE`, `CHECK`) that enforce the
   domain's actual rules, not just its shape.
3. Write migrations — a sequence of files that run in order — rather than a
   single hand-run SQL dump.
4. Load representative sample data and write at least three queries that
   exercise the relationships: a join, an aggregate, and an attempt to
   violate a constraint.
5. Document one deliberate denormalization or indexing decision, if you made
   one, and why.

## Required evidence

- The migration files, committed in the order they run, with git history
  showing them added incrementally
- A terminal transcript or log showing the deliberate constraint violation
  being rejected by the database
- The sample data load script and the three required queries with their
  output
- README documenting each table's purpose and its constraints

## Acceptance criteria

- [ ] The schema has at least one constraint that actively rejects invalid
      sample data, demonstrated by a failing insert.
- [ ] Migrations run in order from an empty database to the final schema
      without manual intervention.
- [ ] At least one query uses a join across two of the tables and returns
      correct results against the sample data.
- [ ] The README documents each table's purpose and its constraints.

## Reflection

Answer these in your own words after doing the work:

1. Which constraint, if you had forgotten it, would have let bad data
   through?
2. What would change in this schema if a fourth entity were added later?

Also record:

- What took longer than expected?
- What would you design differently next time?
- What remains unclear?

## Mentor review guide

- Ask the apprentice to try inserting data that violates a constraint live,
  and explain the error PostgreSQL returns.
- Ask which table would be hardest to change without a migration, and why.

Suggested review outcome: **Approve**, **Request revision**, or **Create
follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes. Solution
generation is not the intended path for this task. Material AI assistance
must be disclosed with the provider/model (if known), purpose, and
verification performed.

## Completion gate

This task is complete only once the evidence is submitted and the mentor
approves the schema — not when the tables merely exist.
