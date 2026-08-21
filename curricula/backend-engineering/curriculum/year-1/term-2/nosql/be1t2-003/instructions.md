# A Document Store for Data That Does Not Fit Tables

**Task ID:** `be1t2-003`
**Estimated effort:** 14 hours
**Module:** NoSQL

## Why this task exists

Not every fact this service will hold is a row with a stable shape.
Audit events, flexible metadata, or activity streams fight a normalized
schema — they either force frequent `ALTER TABLE` work or a pile of
nullable columns. This task adds MongoDB for *that* data, and keeps
PostgreSQL for the invariants you already enforce.

## Authoritative resources

- **MongoDB Manual** (reference): https://www.mongodb.com/docs/manual/
- **PostgreSQL Documentation** (reference): https://www.postgresql.org/docs/current/

Use the MongoDB manual for document shape, indexes, and queries. Use
Postgres docs when you argue why a fact still belongs in a table.

## Work to complete

1. Pick one workload on *this* service that is a poor fit for the
   existing schema — for example an append-only audit log, per-resource
   metadata with a changing shape, or a session/activity history. Write
   the reason down before you open the MongoDB client.
2. Add a MongoDB service to the existing docker-compose file so a clean
   checkout brings up Postgres *and* MongoDB.
3. Define a document convention (required fields, how you name the
   related Postgres id, how you version the shape) and commit two or
   three sample documents that follow it.
4. Implement a Python write path and a read path in the service — an
   HTTP endpoint or a committed script is fine as long as it is
   repeatable.
5. Write a query that filters on a nested field. That query should be
   one that would have needed a new column or a JSONB migration in
   Postgres.
6. Leave the Term 1 entities in PostgreSQL. Do not copy the whole
   relational model into MongoDB "for practice."

The comparison note (what stays in Postgres, and one invariant MongoDB
will not enforce) should be committed before the write path is finished.
That is the process evidence: the decision, then the code.

## Required evidence

- The updated docker-compose file that starts MongoDB next to the
  existing PostgreSQL service
- Sample documents committed as a file, plus the Python read/write path
  that produces them
- Output of a query that filters on a nested field in the collection
- A Markdown note naming one invariant Postgres still enforces that
  MongoDB does not, written before you finished the write path
- Git history showing compose, document shape, and the service path in
  separate commits

Submit a repository URL plus a commit reference. Do not submit only a
screenshot of Compass or a GUI.

## Acceptance criteria

- [ ] `docker compose up` starts MongoDB alongside the existing
      PostgreSQL container from the committed compose file.
- [ ] The running service writes at least one document and reads it
      back through an endpoint or a committed script.
- [ ] A committed query against the collection filters on a nested
      field and the result is pasted in the evidence note.
- [ ] A Markdown note in the repository names one invariant
      PostgreSQL still enforces that the document store does not.

The mentor may ask you to move one Term 1 entity into MongoDB hypothetically
and explain what constraint you would lose.

## Reflection

Answer these in your own words after doing the work:

1. What would break if this document collection were a Postgres table
   instead?
2. What can a client no longer trust MongoDB to reject, that Postgres
   still rejects?
3. How do you join a document back to its relational row, and what
   happens if that row is deleted?

Also record:

- What took longer than expected?
- What would you store in the other database if you started over?
- What remains unclear?

## Mentor review guide

- Confirm the compose file actually starts both databases from a clean
  checkout.
- Ask why the chosen workload is a poor relational fit — reject "I
  needed a MongoDB task" as an answer.
- Open the comparison note's commit date relative to the write-path
  commit; the note should not appear only at the end.

Suggested review outcome: **Approve**, **Request revision**, or **Create
follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes.
Solution generation is not the intended path for this task. Material AI
assistance must be disclosed with the provider/model (if known), purpose,
and verification performed.

## Completion gate

This task is complete only once the evidence is submitted and the mentor
approves the split between stores — not when a MongoDB container merely
runs.
