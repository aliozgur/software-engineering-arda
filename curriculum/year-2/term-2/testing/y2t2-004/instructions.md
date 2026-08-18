# Testing Strategy: Unit to System

**Task ID:** `y2t2-004`  
**Estimated effort:** 16 hours  
**Module:** Testing

## Why this task exists

Choose tests based on risk and feedback value instead of maximizing test count.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- No single mandatory external course. Use official documentation and mentor-curated references appropriate to the task.

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Create a test pyramid/portfolio for an application.
2. Write unit tests for domain logic, integration tests with PostgreSQL and API-level tests.
3. Use test doubles only where justified.
4. Add property-based or fuzz-style testing to one suitable function if tooling permits.
5. Measure test execution time and remove one low-value brittle test.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] Tests can run locally with one command.
- [ ] Integration tests use isolated repeatable data.
- [ ] At least one failure demonstrates each test layer's purpose.
- [ ] Testing strategy document maps risks to tests.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. What should not be mocked?
2. When is an end-to-end test worth its cost?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Break a dependency contract and see which test catches it.

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
