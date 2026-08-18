# Milestone 3: Distributed Telemetry Platform

**Task ID:** `y3t2-006`  
**Estimated effort:** 42 hours  
**Module:** Milestone

## Why this task exists

Build a production-shaped system integrating synchronous and asynchronous components.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- No single mandatory external course. Use official documentation and mentor-curated references appropriate to the task.

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Build ingestion API, message broker workflow, processing worker and PostgreSQL persistence.
2. Use C#/.NET for at least one core service; another component may use Python/TypeScript.
3. Containerize local environment.
4. Implement idempotency, retries and dead-letter handling.
5. Add authentication/authorization, CI, metrics/logs/traces and load tests.
6. Write architecture ADRs and an operations runbook.
7. Demo failure recovery and performance under load.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] System survives duplicate messages without invalid state.
- [ ] A failed dependency produces bounded/recoverable behavior.
- [ ] Telemetry supports diagnosis.
- [ ] Security and load-test evidence are included.
- [ ] Tagged release and demo recording or presentation exist.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. Where is consistency strong and where is it eventual?
2. What would fail first at 10x load?
3. Which component would you remove if simplifying?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Conduct architecture review before final implementation, then chaos-style demo after.

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
