# Capstone Design: Contract, Data Flow and Threat Model

**Task ID:** `be1s-001`
**Estimated effort:** 14 hours
**Module:** Design

## Why this task exists

The rest of the capstone implements one coherent service — the one
you have been building since Term 1 — with a write path that
crosses HTTP, PostgreSQL, RabbitMQ and MongoDB. This task is the
design you will be held to. Implementation comes next; changing
the contract silently later is a revision, not a feature.

## Authoritative resources

- **OpenAPI Specification** (reference): https://spec.openapis.org/oas/latest.html
- **HTTP Semantics - RFC 9110** (deep_dive): https://www.rfc-editor.org/rfc/rfc9110
- **OWASP Top 10** (primary): https://owasp.org/www-project-top-ten/
- **The Twelve-Factor App** (reference): https://12factor.net/

Prefer the specification and OWASP over slide decks. Twelve-Factor
is the bar for how config, backing services and logs are described.

## Work to complete

This is a design task. You may sketch code, but the mentor is
reviewing documents, not a new feature branch.

1. Freeze the capstone HTTP contract in OpenAPI: existing Term 1/2
   routes plus any new routes the integrated write path needs.
   Include auth, error shapes, and status codes you can defend
   from RFC 9110.
2. Write the data flow for *one* successful domain write: which
   process does what, in what order, what is synchronous, and
   what is published for the consumer. Name the hops; do not
   draw a box labelled "backend."
3. Write a threat model as a table: at least four OWASP Top 10
   items, the concrete attack against *this* service, the
   control, and whether that control already exists (point at a
   file) or will be built (point at `be1s-002` / `be1s-003` /
   `be1s-004` / `be1s-005`).
4. Draft the SLO you will operate against: a numeric p95 latency
   and a numeric availability target, plus the metric or log
   query that measures each. Use the load-test baseline from
   `be1t2-006` so the numbers are not invented.
5. Record one design reversal you made while writing — a hop you
   moved, a route you dropped, a control you thought you had and
   did not. Commit that note when it happens, not in a cleanup
   commit at the end.

Do not start the integrated persistence work in this task. If the
design is wrong, the next four tasks will amplify it.

## Required evidence

- An OpenAPI document for every route the capstone will implement,
  plus a validator run pasted in the evidence note
- A data-flow note that names every hop a successful write takes,
  including the queue and the consumer side effect
- A threat-model table mapping at least four OWASP Top 10 items
  to a control that already exists or will be built in a named
  later task
- An SLO file with a numeric latency target, a numeric
  availability target, and the signal you will use to measure each
- Git history showing contract, data flow, threat model, and SLO
  as separate commits, including one design reversal noted
  mid-work

Submit a repository URL plus a commit reference. Do not submit
only a whiteboard photo.

## Acceptance criteria

- [ ] The OpenAPI document validates and lists every route the
      remaining capstone tasks will implement, including error
      responses.
- [ ] The data-flow note names the HTTP handler, the Postgres
      transaction, the publish, the consumer, and the
      document-store write as distinct hops.
- [ ] The threat model maps at least four OWASP Top 10 items to
      a control, each tagged existing or planned with a task id.
- [ ] The SLO names a numeric p95 latency, a numeric availability
      target, and the metric or log query that measures each.

The mentor may refuse the next task until this design is
approved. Expect to defend why a hop is async and why an OWASP
item is marked "existing."

## Reflection

Answer these in your own words after doing the work:

1. What happens to the caller if the broker is down — according
   to this design, not according to hope?
2. Which threat-model row made you least confident, and why?
3. If the SLO is missed next week, which hop do you inspect
   first?

Also record:

- What took longer than expected?
- What would you still change if the mentor asked for a narrower
  capstone?
- What remains unclear?

## Mentor review guide

- Review the contract and the data-flow hops before any
  implementation discussion.
- Ask the apprentice to walk one write without looking at the
  diagram.
- Reject an SLO that has no link to the Term 2 load-test numbers,
  and a threat model that lists OWASP items with no control.

Suggested review outcome: **Approve**, **Request revision**, or
**Create follow-up challenge**. Prefer holding the next task
over approving a vague design.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and
quizzes. Solution generation is not the intended path for this
task. Material AI assistance must be disclosed with the
provider/model (if known), purpose, and verification performed.

## Completion gate

This task is complete only once the evidence is submitted and
the mentor approves the design — not when a set of diagrams
exists.
