# Operate Under an SLO with a Full Container Stack

**Task ID:** `be1s-003`
**Estimated effort:** 18 hours
**Module:** Operate

## Why this task exists

The write path works. This task asks whether you can *see* it
working against the SLO from `be1s-001`, from a compose stack a
teammate can start, with a runbook that does not require you on
the call.

## Authoritative resources

- **OpenTelemetry Documentation** (reference): https://opentelemetry.io/docs/
- **Prometheus Documentation** (reference): https://prometheus.io/docs/introduction/overview/
- **Docker Get Started** (reference): https://docs.docker.com/get-started/
- **The Twelve-Factor App** (reference): https://12factor.net/

Twelve-Factor's logs and backing-services principles apply to
how you run this stack, not just how you wrote the app.

## Work to complete

1. Make `docker compose up` start the API, PostgreSQL, MongoDB
   and RabbitMQ (and the consumer) from a clean checkout, with
   config via environment variables only.
2. Save the SLO queries: request rate, error rate, and p95
   latency. A Prometheus rule file, a Grafana dashboard JSON,
   or committed `promtool`/curl queries are all fine — they
   must run without your laptop's click path.
3. Capture a healthy export of those three signals.
4. Inject one fault you can undo: a handler timeout, a killed
   consumer, or an injected 500 on a chosen route. Capture the
   same three signals afterwards. The fault must show up; if
   it does not, the signals are wrong, not the fault.
5. Write a one-page runbook for "p95 above SLO": the first
   three commands, what each should show, and when to look at
   traces versus the queue. Prefer writing the runbook
   *before* you inject the fault, then amend it with what you
   learned.
6. Record final image size and any `cpus`/`memory` limits on
   the API container. Limits that are only comments do not
   count.

Commit signals and runbook before the fault demonstration.
The fault is a test of the operating kit, not the first time
you look at a graph.

## Required evidence

- The compose file and a clean-checkout transcript of the full
  stack coming up
- A committed dashboard definition or saved queries for
  request rate, error rate, and p95, plus a scrape or export
  from a healthy run
- A fault demonstration (timeout, killed consumer, or injected
  500) with the same signals showing the change
- A runbook file listing the first three commands for a
  p95-over-SLO page, written before the fault demo if possible
- README reporting image size and container resource limits,
  with Git history showing signals before the fault injection

Submit a repository URL plus a commit reference. Do not submit
only a screenshot of Grafana.

## Acceptance criteria

- [ ] `docker compose up` starts the API, PostgreSQL, MongoDB
      and RabbitMQ from a clean checkout.
- [ ] A committed dashboard definition or query file shows
      request rate, error rate, and p95 against the SLO from
      `be1s-001`.
- [ ] A deliberate fault is visible as a change in at least
      one of those three signals, with before and after
      exports committed.
- [ ] The runbook file lists the first three commands to run
      when p95 exceeds the SLO, and those commands exist in
      the repository.

The mentor may pick a different fault than the one you
documented and ask you to apply the runbook anyway.

## Reflection

Answer these in your own words after doing the work:

1. Which signal moved first when you injected the fault, and
   which one stayed flat?
2. What did the runbook get wrong before you amended it?
3. What resource limit would you tighten first in a real
   environment, and what would you measure to decide?

Also record:

- What took longer than expected?
- What would you add to compose before handing this to a
  teammate?
- What remains unclear?

## Mentor review guide

- Tear the stack down and bring it up from the committed
  instructions only.
- Ask the apprentice to execute the first runbook command
  live.
- Reject a dashboard that cannot be recreated from the
  repository, and a fault that never appears in the signals.

Suggested review outcome: **Approve**, **Request revision**,
or **Create follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and
quizzes. Solution generation is not the intended path for
this task. Material AI assistance must be disclosed with the
provider/model (if known), purpose, and verification
performed.

## Completion gate

This task is complete only once the evidence is submitted
and the mentor approves the demonstrated operating kit —
not when compose merely starts.
