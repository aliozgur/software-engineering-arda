# Production API with ASP.NET Core

**Task ID:** `y3t1-002`  
**Estimated effort:** 22 hours  
**Module:** Backend

## Why this task exists

Build a production-shaped backend rather than a CRUD tutorial.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **.NET and C# Documentation** (reference): https://learn.microsoft.com/dotnet/
- **OpenAPI Specification** (reference): https://spec.openapis.org/oas/latest.html

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Implement a versioned HTTP API with ASP.NET Core and PostgreSQL.
2. Use validation, consistent errors and OpenAPI.
3. Implement authentication/authorization using a standards-based approach appropriate to the lab.
4. Add migrations and transaction boundaries.
5. Add integration tests against a real PostgreSQL test instance.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] Authorization is enforced server-side.
- [ ] API errors are consistent and do not leak sensitive detail.
- [ ] Integration tests cover authorization and transaction behavior.
- [ ] OpenAPI is usable by a client.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. Where should transaction boundaries live?
2. Authentication versus authorization?
3. Which API changes are breaking?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Attempt unauthorized access and malformed requests during review.

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
