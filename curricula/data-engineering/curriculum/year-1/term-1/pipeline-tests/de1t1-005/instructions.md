# Test the Transform, Not the Warehouse Screenshot

**Task ID:** `de1t1-005`
**Estimated effort:** 8 hours
**Module:** Pipeline Tests

## Why this task exists

Quality in this path is a gate on movement, not an exploratory notebook.
You are testing that a transform keeps grain, rejects impossible rows, and
that PostgreSQL still enforces the constraint you claimed in DDL.

This is adjacent to data quality as a discipline: missingness and invalid
values are handled as rules the pipeline must enforce, not as charts of
null rates for a report.

## Authoritative resources

- **Python 3 Tutorial** (reference): https://docs.python.org/3/tutorial/
  — `unittest` / `pytest` style functions, fixtures, assertions.
- **PostgreSQL Documentation** (reference): https://www.postgresql.org/docs/current/
  — unique and foreign-key constraints.

Use official documentation as the primary source. If you use anything else,
record it in your notes.

## Work to complete

1. Extract transform logic into functions that can run on in-memory rows
   or fixtures without a live warehouse.
2. Write at least five automated tests covering all of:
   - uniqueness of the natural key
   - a required field that must not be null
   - referential integrity to a dimension or parent key
   - row-count conservation, or a filter whose dropped-row count is
     asserted
   - one business rule (for example amount >= 0, or status in an allowed
     set)
3. Keep a bad fixture that a naive load would accept. Run the suite
   against it and capture at least one named test failing. The failure
   message must name the rule.
4. Keep at least two tests database-free. Add at least one integration
   test that hits PostgreSQL and depends on a real unique or foreign-key
   constraint.
5. Document one command that runs the happy suite.

## Required evidence

- The documented test command and a captured passing run of at least five
  tests
- A captured failing run against a bad fixture, with the failure message
  naming the violated rule
- The two (or more) tests that run without a database, and the one that
  hits PostgreSQL
- A listing or query showing the unique or foreign-key constraint the
  integration test depends on
- Reflection notes answering the questions below

Submit a repository URL plus a commit reference. Screenshots of a green
bar without the command output are not enough.

## Acceptance criteria

- [ ] At least five automated tests run from one documented command, and a
      captured run shows them passing on the happy fixture.
- [ ] A second captured run against a bad fixture shows at least one named
      test failing, and the failure message names the violated rule.
- [ ] At least two tests execute the transform without opening a database
      connection.
- [ ] At least one test runs against PostgreSQL and would fail if a
      required unique or foreign-key constraint were absent, shown by a
      captured constraint listing or a captured failure after dropping that
      constraint in a disposable database.

The mentor may hand you a sixth bad row and ask which existing test should
fail. If the answer is "none, but I would notice," the suite is not a
gate.

## Reflection

Answer these in your own words after doing the work:

1. Which rule cannot be tested without PostgreSQL, and why?
2. What would still get into the warehouse if you only ran the
   database-free tests?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you learned the objective?

## Mentor review guide

Ask the apprentice to drop the unique constraint on a disposable database
and rerun the integration test. If it still passes, the test was asserting
Python state, not the warehouse. Do not approve tests that only check
`len(df) > 0`.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is
not the intended path for this task. The apprentice must be able to name
what each test fails on without reading the model output. Material AI
assistance must be recorded in the submission notes with the
provider/model (if known), purpose, and verification performed.

## Completion gate

This task is not complete when the happy suite is green. It is complete
once the failing-fixture capture and the PostgreSQL-backed test are
submitted and the mentor approves the demonstrated competency.
