# API Evolution, Compatibility and Contracts

**Task ID:** `y3t2-005`  
**Estimated effort:** 12 hours  
**Module:** Api Design

## Why this task exists

Learn to evolve interfaces without casually breaking consumers.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **OpenAPI Specification** (reference): https://spec.openapis.org/oas/latest.html
- **Semantic Versioning 2.0.0** (reference): https://semver.org/

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Take an existing API and propose a new requirement that changes its model.
2. Classify changes as compatible or breaking.
3. Implement contract tests.
4. Design a deprecation path.
5. Version a client and server through at least one compatible evolution.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] Compatibility matrix exists.
- [ ] Deprecation has timeline/communication concept.
- [ ] Contract tests catch a deliberate break.
- [ ] Apprentice distinguishes API version from application release version.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. Can adding a field be breaking? Under what client assumptions?
2. What makes distributed upgrades difficult?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Run old client against new server during review.

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
