# HTTP and API Fundamentals

**Task ID:** `y1t2-005`  
**Estimated effort:** 12 hours  
**Module:** Http Api

## Why this task exists

Understand HTTP as a protocol, not just a library call.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **MDN Web Docs** (reference): https://developer.mozilla.org/
- **HTTP Semantics - RFC 9110** (deep_dive): https://www.rfc-editor.org/rfc/rfc9110
- **OpenAPI Specification** (reference): https://spec.openapis.org/oas/latest.html

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Capture and annotate an HTTP request/response.
2. Build a minimal Python HTTP API.
3. Use appropriate methods, status codes, headers and JSON representations.
4. Describe the API with a small OpenAPI document.
5. Implement consistent error responses and input validation.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] API contract and implementation agree.
- [ ] Status codes are defensible.
- [ ] Errors do not expose stack traces or secrets.
- [ ] A curl-based smoke test is included.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. What makes an operation idempotent?
2. When is POST appropriate versus PUT?
3. What is the difference between transport success and application success?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Give three API scenarios and ask apprentice to choose method/status semantics.
- Review contract before implementation details.

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
