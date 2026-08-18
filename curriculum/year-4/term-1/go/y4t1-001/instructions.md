# Go for Networked and Concurrent Services

**Task ID:** `y4t1-001`  
**Estimated effort:** 20 hours  
**Module:** Go

## Why this task exists

Learn a second systems-oriented service language and its concurrency model.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **Go Tutorials** (reference): https://go.dev/doc/tutorial/

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Complete Go getting-started/module/tutorial material and Tour sections relevant to concurrency.
2. Build a small HTTP/TCP service.
3. Use goroutines/channels where they simplify coordination rather than as decoration.
4. Use context cancellation and timeouts.
5. Write tests and run race detection.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] go test passes; race detector is clean for tested paths.
- [ ] Cancellation is propagated.
- [ ] Errors are handled idiomatically.
- [ ] Apprentice can compare Go concurrency with C# async/tasks and OS threads.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. When should a channel not be used?
2. How does context cancellation improve service behavior?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Introduce a shutdown requirement and review graceful termination.

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
