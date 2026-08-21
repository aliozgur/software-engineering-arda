# A REST API Backed by PostgreSQL

**Task ID:** `be1t1-004`
**Estimated effort:** 20 hours
**Module:** Backend

## Why this task exists

Up to now the API and the schema have been separate exercises. This task
forces them to agree with each other: the routes you implement, the
constraints the database enforces, and the OpenAPI document you write all
have to describe the same thing, or an actual client of this API will hit a
mismatch the first time it's used for real.

## Authoritative resources

- **PostgreSQL Documentation** (reference): https://www.postgresql.org/docs/current/
- **OpenAPI Specification** (reference): https://spec.openapis.org/oas/latest.html
- **Python 3 Tutorial** (reference): https://docs.python.org/3/tutorial/

## Work to complete

1. Implement CRUD endpoints for the domain's main entities using a Python web
   framework of your choice (for example FastAPI or Flask) against the
   PostgreSQL schema from the previous task.
2. Validate all input and return a consistent error shape for validation
   failures.
3. Wrap any operation that touches more than one table in a transaction.
4. Write an OpenAPI document describing every implemented route, including
   request/response schemas and error responses.
5. Write a script or automated check that confirms the OpenAPI document's
   routes match the routes actually implemented.

## Required evidence

- Git history showing the API, validation, and OpenAPI document built
  incrementally rather than in one commit
- The OpenAPI document file committed to the repository, plus confirmation
  it validates (a CLI or online validator run)
- A test or script output demonstrating the transaction rollback on a
  simulated failure
- curl or automated test output showing a validation failure producing the
  documented error shape

## Acceptance criteria

- [ ] Every implemented route appears in the OpenAPI document with matching
      request and response schemas.
- [ ] An operation that touches more than one table is wrapped in a
      transaction, demonstrated by a rollback test.
- [ ] Invalid input produces a 4xx response with a validation error body,
      not a 500.
- [ ] The OpenAPI document validates against the OpenAPI schema.

## Reflection

Answer these in your own words after doing the work:

1. Where did the API contract and the implementation disagree the first
   time you checked them against each other?
2. What forced the transaction boundary you chose — what would have gone
   wrong without it?
3. Which API changes would break a client, and which wouldn't?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?

## Mentor review guide

- Attempt malformed requests and a simulated mid-transaction failure during
  review.
- Ask the apprentice to point at the exact line in the OpenAPI document that
  would catch a mismatch if the implementation drifted.

Suggested review outcome: **Approve**, **Request revision**, or **Create
follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes. Solution
generation is not the intended path for this task. Material AI assistance
must be disclosed with the provider/model (if known), purpose, and
verification performed.

## Completion gate

This task is complete only once the evidence is submitted and the mentor
approves the demonstrated agreement between contract and implementation.
