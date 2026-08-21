# Designing for Failure and Controlled Degradation

**Task ID:** `sa1t2-004`
**Estimated effort:** 8 hours
**Module:** Failure

## Why this task exists

Term 2 has so far chosen stores and sized the happy path. This task asks what
the system does when a dependency is slow, down, or lying. Timeouts and retries
are architecture: they decide whether a single slow call stays a single slow
call or becomes a retry storm that takes the rest of the system with it. The
user-visible degradation is part of the decision — "fail closed," "serve stale,"
and "queue for later" are different products, not different polish.

Reading about circuit breakers is preparation. Completion requires a table with
numbers, an ADR for the retry budget, and one dependency you can defend not
retrying.

## Authoritative resources

- **The Twelve-Factor App** (supporting): https://12factor.net/ — disposability
  and backing services are the properties that make a timeout-and-restart story
  honest. If a factor does not apply to a dependency, say so in the notes.

Use official documentation as the primary source. If you use other material,
record it in your notes.

## Work to complete

1. Take the system from `sa1t2-001` (or a mentor-assigned brief). List at least
   three runtime dependencies — a datastore, an upstream HTTP API, a queue or
   mail provider, a cache, an identity service. Name each as a backing service,
   not as "the database" in the abstract.
2. For each dependency, fill a row: the failure you are designing for (timeout,
   refused connection, stale replica, poison message), a timeout number in
   milliseconds or seconds, and what the user sees or what the system continues
   to do. At least two rows must name a degradation other than a generic error
   page (serve last-known data, skip an optional enrichment, enqueue for later,
   fail the write).
3. Write an ADR for the retry policy on the dependency you are most tempted to
   retry forever. State maximum attempts and backoff. Name the NFR that budget
   is not allowed to exceed — an end-to-end latency target, an availability
   SLO-to-be, or a retry-amplification ceiling such as "retries must not more
   than double offered load."
4. Mark at least one dependency non-retryable. The reason must be a side
   effect (a payment capture, an email send), a missing idempotency key, or a
   cascade risk — not "it is simpler."

## Required evidence

- A failure-mode table covering at least three dependencies, each with a named
  failure, a timeout in milliseconds or seconds, and the user-visible
  degradation
- An ADR stating the retry budget (maximum attempts and backoff) and the NFR
  that budget is not allowed to exceed
- A note marking at least one dependency as non-retryable, with a reason that
  is not "it is simpler not to retry"

Submit a repository URL plus a commit reference. Keep the table and the ADR
as separate commits or clearly separated files.

## Acceptance criteria

- [ ] At least three dependencies each have a named failure mode, a timeout
      number, and a user-visible degradation that is not "show an error page"
      for every row.
- [ ] The ADR states a retry budget as maximum attempts plus backoff, and names
      the NFR that budget must not exceed.
- [ ] At least one dependency is marked non-retryable with a reason tied to a
      side effect, an idempotency gap, or a cascade risk.

## Reflection

1. Which timeout, if you set it 10x larger, would hide a problem rather than
   absorb a blip — and how do you know?
2. If the non-retryable dependency starts succeeding on the second try in
   production, what would have to be true before you would reverse that row?

Also record: what took longer than expected, what you'd practice again, what
remains unclear.

## Mentor review guide

- Pick the shortest timeout and ask what happens when the dependency is slow
  but still succeeding just after that number. Listen for retry amplification
  and for whether the user-visible path is specified.
- Do not approve a table where every degradation is the same sentence.

Suggested outcome: **Approve**, **Request revision**, or **Discuss live**.

## AI use policy

Mode: **guided**. AI may explain timeout and retry terminology and quiz your
understanding of retry amplification. AI must not fill the table or write the
ADR for your specific dependencies. Disclose any material AI use.

## Completion gate

This task is not complete when three rows exist. It is complete once you can
state, unprompted, which call you will not retry and which NFR the retries you
do allow are not permitted to break.
