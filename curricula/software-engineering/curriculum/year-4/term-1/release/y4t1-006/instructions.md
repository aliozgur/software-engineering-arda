# Dependency and Supply-Chain Hygiene

**Task ID:** `y4t1-006`  
**Estimated effort:** 12 hours  
**Module:** Release

## Why this task exists

Treat dependencies and build inputs as part of the product's risk surface.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- No single mandatory external course. Use official documentation and mentor-curated references appropriate to the task.

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Inventory direct dependencies in one project.
2. Identify licenses and known-vulnerability tooling available for the ecosystem.
3. Pin/lock dependencies appropriately.
4. Create an automated dependency/security check.
5. Document update policy and emergency patch process.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] Dependency inventory is reproducible.
- [ ] No secrets in build configuration.
- [ ] Lockfiles are committed where ecosystem expects them.
- [ ] Policy distinguishes routine update from urgent security response.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. What risk comes from transitive dependencies?
2. Why can 'latest' harm reproducibility?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask apprentice to evaluate one dependency removal/replacement.

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
