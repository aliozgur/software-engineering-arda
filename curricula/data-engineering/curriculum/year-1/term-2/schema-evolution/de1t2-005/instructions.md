# Evolve a Schema Without Breaking Yesterday's Consumer

**Task ID:** `de1t2-005`
**Estimated effort:** 8 hours
**Module:** Schema Evolution

## Why this task exists

You already wrote a contract and a stream sink. Producers will still
change the payload. The engineering problem is coexistence: last week's
consumer and this week's producer, or the reverse, for a documented
window.

Additive changes should pass through. Breaking changes should fail
loudly or ride a shim you can name. Silent coercion is how a string
becomes a number becomes null becomes a wrong grain.

## Authoritative resources

- **Apache Kafka Documentation** (reference): https://kafka.apache.org/documentation/
  — versioned topics, headers, or a payload `schema_version` field are
  all valid; pick one and use it.
- **PostgreSQL Documentation** (reference): https://www.postgresql.org/docs/current/
  — additive warehouse columns, and why a type change on a loaded column
  is not free.

Use official documentation as the primary source. If you use anything else,
record it in your notes. A file-backed fixture of versioned payloads is
acceptable if it drives the same consumer code as the stream path.

## Work to complete

1. Freeze a v1 payload and a v1 consumer that loads it under the
   existing contract.
2. Ship an additive change: a new optional field. Keep the old consumer
   deployed. It must process both a captured v1 batch and a v2 batch
   that only adds that field.
3. Ship a breaking change: a type change on a required field, or a
   rename of a required field. Options: dual-write, a versioned
   topic/queue, or an explicit incompatibility window. The old consumer
   on a breaking payload must not write a corrupt warehouse row —
   reject with a logged error, or decode through a shim that you
   document.
4. Keep a contract changelog with v1, the additive version, and the
   breaking version. The breaking entry has a date or reason.
5. Replay v1 payloads after the additive change is deployed. They still
   load. Capture that as a test or a recorded replay.

## Required evidence

- Contract changelog listing v1, the additive version, and the breaking
  version with reason
- A captured run of the old consumer successfully processing a payload
  that only adds an optional field
- A captured run of the old consumer facing a breaking payload without
  writing a corrupt warehouse row
- A test or replay showing v1 payloads still load after the additive
  change is deployed
- Reflection notes answering the questions below

Submit a repository URL plus a commit reference.

## Acceptance criteria

- [ ] The old consumer successfully processes a v2 payload that only
      adds an optional field, shown by a captured row or log.
- [ ] The old consumer encountering a breaking payload does not write a
      corrupt warehouse row: it rejects with a logged error or reads a
      compatibility shim, and the captured warehouse sample shows no
      truncated or mistyped required field.
- [ ] The contract changelog lists v1, the additive version, and the
      breaking version with a date or reason on the breaking entry.
- [ ] A test or replay shows v1 payloads still load after the additive
      change is deployed.

The mentor may hand you a third payload and ask you to classify it
before running. If "JSON will figure it out" is the answer, request
revision.

## Reflection

Answer these in your own words after doing the work:

1. What made the breaking change breaking, in one sentence a producer
   could use as a checklist item?
2. How long could v1 and the additive v2 coexist in your design, and
   what artifact tells operators that window is over?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you learned the objective?

## Mentor review guide

Ask the apprentice to corrupt one required field's type live and show
the reject or shim. Do not approve "we deployed producer and consumer
in the same commit, so compatibility does not matter."

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is
not the intended path for this task. The apprentice must classify
additive versus breaking without the model. Material AI assistance must
be recorded in the submission notes with the provider/model (if known),
purpose, and verification performed.

## Completion gate

This task is not complete when a new field exists. It is complete once
the old-consumer additive success, the breaking-payload non-corruption,
the changelog, and the v1 replay are submitted and the mentor approves
the demonstrated competency.
