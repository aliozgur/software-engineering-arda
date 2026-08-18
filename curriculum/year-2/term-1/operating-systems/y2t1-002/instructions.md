# Processes, System Calls and Isolation

**Task ID:** `y2t1-002`  
**Estimated effort:** 18 hours  
**Module:** Operating Systems

## Why this task exists

Understand how applications cross the user/kernel boundary and how processes are isolated.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **MIT 6.1810 - Operating System Engineering** (primary): https://pdos.csail.mit.edu/6.1810/

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Study xv6/MIT material on processes and system calls.
2. Trace a simple system call from user code into kernel code.
3. Write a small C program using fork/exec/wait or platform equivalents in a Unix environment.
4. Inspect processes, file descriptors and exit status.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] Trace document names relevant source paths/functions.
- [ ] Program demonstrates parent/child behavior.
- [ ] Apprentice explains process versus program.
- [ ] Failure and cleanup behavior are handled.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. Why are system calls controlled entry points?
2. What state is duplicated or shared after fork?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask apprentice to predict output/order for a modified process program.

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
