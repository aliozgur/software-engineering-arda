# Automated Testing for the Service

**Task ID:** `be1t1-005`
**Estimated effort:** 14 hours
**Module:** Testing

## Why this task exists

A test suite that only exercises the happy path will pass right up until the
first real user sends something unexpected. This task is about proving the
service's failure modes are handled on purpose, not just that its success
path works once.

## Authoritative resources

- **Python 3 Tutorial** (reference): https://docs.python.org/3/tutorial/

## Work to complete

1. Set up a dedicated test database (a separate schema or instance from your
   development database) with a reliable way to reset its state between
   runs.
2. Write unit tests for validation logic in isolation from the database.
3. Write integration tests against the real test database covering at least
   two failure modes: a constraint violation, a not-found lookup, or a
   conflicting update.
4. Add a dedicated test for the transaction rollback behavior built in the
   previous task — one that fails if the rollback is ever removed.
5. Measure and report test coverage, and justify in writing any area you
   deliberately left untested.

## Required evidence

- Git history showing tests added incrementally alongside or after each
  feature
- Full test run output (for example `pytest -v`) pasted into the evidence
  note
- The coverage report output or file
- README section explaining any deliberately untested area

## Acceptance criteria

- [ ] Integration tests run against a real PostgreSQL instance and reset its
      state between runs.
- [ ] At least two tests intentionally trigger a failure mode and assert on
      the resulting error, not just the happy path.
- [ ] The transaction rollback behavior has a dedicated test that fails if
      the rollback is removed.
- [ ] A coverage report is generated and any gap over 10% in a core module
      is explained in the README.

## Reflection

Answer these in your own words after doing the work:

1. Which test caught a real bug while you were writing it?
2. What edge case did you almost skip, and why did you decide to keep it?

Also record:

- What took longer than expected?
- What would you test differently next time?
- What remains unclear?

## Mentor review guide

- Ask the apprentice to remove the transaction rollback temporarily and show
  the dedicated test failing.
- Pick one "deliberately untested" area from the README and ask why it was
  excluded.

Suggested review outcome: **Approve**, **Request revision**, or **Create
follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes. Solution
generation is not the intended path for this task. Material AI assistance
must be disclosed with the provider/model (if known), purpose, and
verification performed.

## Completion gate

This task is complete only once the evidence is submitted and the mentor
approves the demonstrated failure-mode coverage — not when the suite is
merely green.
