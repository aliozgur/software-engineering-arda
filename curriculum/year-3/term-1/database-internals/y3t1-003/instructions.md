# Database Systems: Storage and Indexes

**Task ID:** `y3t1-003`  
**Estimated effort:** 24 hours  
**Module:** Database Internals

## Why this task exists

Understand why database engines behave as they do.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **CMU 15-445/645 - Database Systems** (primary): https://15445.courses.cs.cmu.edu/

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Study CMU material on storage, buffer pools and indexes.
2. Implement a simplified page/cache or B+tree exercise, or complete appropriate BusTub project portions if licensing/course rules permit.
3. Compare B-tree and hash index workloads conceptually and experimentally.
4. Write a note connecting buffer management to OS/filesystem caching.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] Implementation has tests.
- [ ] Data structure invariants are documented.
- [ ] Experiment uses multiple workload shapes.
- [ ] Apprentice explains why database pages and buffer pools exist.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. What is the cost model behind an index lookup?
2. Why can double buffering occur?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Whiteboard a page lookup from query to storage.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that
force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **restricted**

AI may be used for explanation, hints, quizzes and review unless the mentor further restricts it. Solution generation
is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must
be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the
mentor approves the demonstrated competency.
