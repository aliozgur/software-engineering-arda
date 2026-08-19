# Networking II: TCP, UDP, Sockets and TLS

**Task ID:** `y2t1-006`  
**Estimated effort:** 22 hours  
**Module:** Networking

## Why this task exists

Understand reliable transport, sockets and secure channels through implementation and capture.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **Stanford CS144 - Introduction to Computer Networking** (primary): https://cs144.github.io/
- **HTTP Semantics - RFC 9110** (deep_dive): https://www.rfc-editor.org/rfc/rfc9110

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Build TCP echo client/server and UDP counterpart.
2. Capture connection establishment, data transfer and close.
3. Simulate delay/loss where practical and observe behavior.
4. Inspect a TLS connection at a conceptual/certificate level.
5. Document TCP reliability, flow control and congestion-control distinction.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] Socket programs handle disconnects.
- [ ] Capture identifies handshake and sequence/ack behavior.
- [ ] TCP versus UDP choice is reasoned.
- [ ] TLS notes distinguish encryption, authentication and certificates.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. Why can TCP be reliable while IP is best effort?
2. When is UDP a better foundation?
3. What does TLS not protect?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask apprentice to diagnose a connection failure using only logs and packet capture.

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
