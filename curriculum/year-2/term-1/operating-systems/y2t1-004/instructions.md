# Virtual Memory and Filesystems

**Task ID:** `y2t1-004`  
**Estimated effort:** 20 hours  
**Module:** Operating Systems

## Why this task exists

Understand address translation, paging, persistence and filesystem abstractions.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **MIT 6.1810 - Operating System Engineering** (primary): https://pdos.csail.mit.edu/6.1810/

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Study page tables, virtual memory and filesystem sections/labs appropriate to current ability.
2. Draw a virtual-to-physical translation example.
3. Measure process memory while allocating/touching memory.
4. Inspect filesystem metadata, permissions and links.
5. Write a short comparison of buffered I/O, filesystem cache and durable storage.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] Diagrams are technically coherent.
- [ ] Measurements distinguish reserved/virtual from resident concepts.
- [ ] Filesystem experiment is reproducible.
- [ ] Apprentice can explain why write() returning does not always imply durable media.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. What benefits does virtual memory provide besides 'more memory'?
2. What failures can occur between application write and durable storage?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Use scenario questions involving page faults and file rename/crash semantics.

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
