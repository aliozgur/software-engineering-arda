# PostgreSQL: Transactions, Indexes and EXPLAIN

**Task ID:** `y1t2-003`  
**Estimated effort:** 14 hours  
**Module:** Postgresql

## Why this task exists

Move from writing SQL to reasoning about database behavior.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **Harvard CS50 SQL - Introduction to Databases with SQL** (primary): https://cs50.harvard.edu/sql/
- **PostgreSQL Documentation** (reference): https://www.postgresql.org/docs/current/

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Load a dataset large enough to measure query behavior.
2. Create and compare queries before/after indexes using EXPLAIN ANALYZE.
3. Demonstrate a transaction rollback.
4. Run two sessions to observe transaction isolation behavior.
5. Document one index that helps and one unnecessary index.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] Measurements are recorded.
- [ ] EXPLAIN output is interpreted in apprentice's own words.
- [ ] Transaction demo is reproducible.
- [ ] Index choices reference workload, not blanket rules.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. Why can an index slow writes?
2. What anomaly is isolation trying to control?
3. Why is 'query uses index' not equivalent to 'query is fast'?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask for a live EXPLAIN of a new query.
- Probe understanding of transaction boundaries.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that
force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, quizzes and review unless the mentor further restricts it. Solution generation
is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must
be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the
mentor approves the demonstrated competency.
