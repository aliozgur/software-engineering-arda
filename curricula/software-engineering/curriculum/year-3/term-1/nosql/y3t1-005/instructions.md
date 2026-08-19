# MongoDB and Document Data Modelling

**Task ID:** `y3t1-005`  
**Estimated effort:** 12 hours  
**Module:** Nosql

## Why this task exists

Learn when document modelling is appropriate by comparing it with relational design.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **MongoDB Manual** (reference): https://www.mongodb.com/docs/manual/

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Model the same small domain in PostgreSQL and MongoDB.
2. Choose embed versus reference relationships deliberately.
3. Create indexes for demonstrated query patterns.
4. Implement a small application query layer.
5. Write a decision memo identifying when MongoDB is and is not preferable.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] Decision memo discusses consistency, joins/aggregation, schema evolution and workload.
- [ ] Indexes match actual queries.
- [ ] No claim that NoSQL means 'no schema'.
- [ ] Apprentice can identify duplicated-data update risks.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. Which domain aggregate fits a document naturally?
2. What problem would force you back toward relational constraints?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Change a query requirement and ask how each model adapts.

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
