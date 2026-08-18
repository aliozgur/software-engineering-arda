# Understand Git, Don't Memorize It

**Task ID:** `y1t1-002`  
**Estimated effort:** 8 hours  
**Module:** Git

## Why this task exists

Understand commits, trees, blobs, references and the working tree so Git commands have a mental model.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **MIT - The Missing Semester of Your CS Education (2026)** (primary): https://missing.csail.mit.edu/2026/
- **Pro Git (official Git book)** (reference): https://git-scm.com/book/en/v2

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Create a repository with meaningful commits.
2. Draw the commit graph before and after branching/merging.
3. Inspect objects with git cat-file and references with git show-ref.
4. Create a merge conflict deliberately, resolve it and explain the result.
5. Perform a rebase on a disposable branch and compare commit hashes.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] Repository contains meaningful history, not one final commit.
- [ ] A Markdown note explains working tree, index, HEAD, branch and commit.
- [ ] Conflict resolution is documented.
- [ ] Apprentice can explain why rebase changes commit IDs.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. Merge versus rebase: when would you choose each?
2. Why is force-pushing dangerous?
3. What does Git store that a normal folder copy does not?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask for a live recovery from a mistaken commit using reflog.
- Do not approve if the apprentice only knows command recipes.

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
