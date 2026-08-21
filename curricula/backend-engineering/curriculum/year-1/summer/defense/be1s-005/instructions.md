# Capstone Defense: Inject a Failure and Recover

**Task ID:** `be1s-005`
**Estimated effort:** 18 hours
**Module:** Defense

## Why this task exists

This is the capstone milestone. The mentor is no longer asking
whether a feature exists. They are asking whether you can
break the service you built, bring it back, and account for
the writes that were in flight. LEARN BY DOING. GROW THROUGH
MENTORSHIP — this is the doing that the rest of the path was
for.

## Authoritative resources

- **RabbitMQ Tutorials** (reference): https://www.rabbitmq.com/tutorials
- **MongoDB Manual** (reference): https://www.mongodb.com/docs/manual/
- **PostgreSQL Documentation** (reference): https://www.postgresql.org/docs/current/

You already have the operating kit from `be1s-003` and the
release tag from `be1s-004`. Use those. The manuals are for
the failure modes of each backing service.

## Work to complete

The mentor may pick which two failures you run first. Prepare
all three.

1. Write a short drill script or a checked-in step file for
   each failure mode:
   - stop or partition RabbitMQ
   - stop MongoDB
   - inject latency on a hot path (application fault, delayed
     handler, or a constrained query)
2. For each chosen failure: start from the tagged release,
   inject, capture logs and SLO signals, recover, capture
   again. Do not rebuild the schema by hand to "get back to
   green."
3. During one failure, issue a domain write that is in flight
   when the fault lands. After recovery, say whether that
   write is in PostgreSQL. If it is missing, that loss must
   match the `be1s-001` design (and you must say so). If it
   is present in Postgres but not in MongoDB, say how you
   will drain or replay.
4. Write the post-incident note *from the logs*: start time,
   detection time (when a signal moved), mitigation time,
   impact on the SLO, what you would change in design or
   runbook. Timestamps in the note must appear in the
   committed logs.
5. Finish with a smoke request against the recovered API.
   The service serving again is part of the evidence, not
   implied.

Commit the drill steps first, then each failure's artifacts,
then the write-up. A single retrospective written after a
private drill is not process evidence.

## Required evidence

- Logs or exports for at least two of: broker down, MongoDB
  down, injected latency — each with a recovery
- A write-accounting note for one in-flight write: present
  in PostgreSQL, or explicitly lost, with the reason
- A post-incident note whose timeline timestamps come from
  the logs, not from memory, and that states SLO impact
- Git history showing the drill script or steps, the first
  failure, the second failure, and the write-up as separate
  commits
- A transcript showing the API serving requests after
  recovery without a manual schema rebuild

Submit a repository URL plus a commit reference. Do not
submit only a narrative with no logs.

## Acceptance criteria

- [ ] At least two of the three failure modes (broker down,
      document store down, injected latency) are demonstrated
      with committed logs and a recovery for each.
- [ ] After recovery, one in-flight write is either present
      in PostgreSQL or documented as lost with a reason that
      matches the `be1s-001` design.
- [ ] The post-incident note includes a timeline whose
      timestamps appear in the committed logs, plus whether
      the SLO was missed.
- [ ] After recovery the API serves a documented smoke
      request without a manual schema rebuild or a restore
      from an undocumented backup.

The mentor may inject the third failure live and ask you to
apply the runbook from `be1s-003` without opening your
notes first.

## Reflection

Answer these in your own words after doing the work:

1. Which failure was harder to *see* than to recover from?
2. What would you change in `be1s-001` after watching a
   write sit in only one store?
3. What would you still refuse to automate, and why does
   that need a person?

Also record:

- What took longer than expected?
- What would you drill again in a month?
- What remains unclear?

## Mentor review guide

- Pick the failure the apprentice looks least comfortable
  with, if they only prepared two.
- Ask them to account for the in-flight write using logs,
  not recollection.
- Reject a post-incident note whose times do not appear in
  the logs, and a recovery that rebuilds the database from
  scratch.

Suggested review outcome: **Approve**, **Request revision**,
or **Create follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and
quizzes. Solution generation is not the intended path for
this task. Material AI assistance must be disclosed with
the provider/model (if known), purpose, and verification
performed.

## Completion gate

This task is complete only once the evidence is submitted
and the mentor approves the demonstrated recovery — not
when a post-incident document exists.
