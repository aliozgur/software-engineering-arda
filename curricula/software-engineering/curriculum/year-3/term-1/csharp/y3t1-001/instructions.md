# C# and .NET Engineering Foundations

**Task ID:** `y3t1-001`  
**Estimated effort:** 20 hours  
**Module:** Csharp

## Why this task exists

Use a statically typed managed platform to deepen API, concurrency and maintainability skills.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **.NET and C# Documentation** (reference): https://learn.microsoft.com/dotnet/

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Build a .NET console/library solution using modern C#.
2. Use nullable reference types, records/classes appropriately and dependency injection only where it adds value.
3. Write unit tests.
4. Implement async I/O with cancellation tokens.
5. Package configuration and structured logging cleanly.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] Warnings are treated seriously.
- [ ] Async methods do not block with .Result/.Wait in application paths.
- [ ] Cancellation propagates.
- [ ] Public API choices are documented.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. What does the type system prevent that Python does not?
2. Where can async code still create concurrency problems?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask apprentice to trace cancellation and exception propagation.

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
