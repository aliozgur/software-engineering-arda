# Trace a Request Path with OpenTelemetry

**Task ID:** `pd1t2-004`
**Estimated effort:** 13 hours
**Module:** Tracing

## Why this task exists

Metrics tell you *that* something got slower. A trace tells you *where* in the path. Term 3 will ask you to diagnose a bad release; you need at least one request that produced two spans you can name from the code, exported to a backend that runs on your machine.

This is an apprenticeship task, not a content-consumption checkbox. Reading OpenTelemetry docs is only preparation. Completion requires a trace id a mentor can look up.

## Authoritative resources

- **OpenTelemetry Documentation** (reference): https://opentelemetry.io/docs/

Use the official OpenTelemetry documentation for your language. Run a local collector and a local UI (Jaeger, Zipkin, or the collector's debug/file exporter). Do not require a paid APM product.

## Work to complete

Instrument the same service you scrape in `pd1t2-003`.

1. Add OpenTelemetry SDK or documented auto-instrumentation. Commit the dependency and the initialization code.
2. Export spans to a local backend. Commit the collector or exporter config. Document how to start it.
3. Send one documented request that crosses at least two span boundaries (HTTP handler plus an outbound call, a dependency query, or a clearly named internal span you added).
4. Capture the trace. Record the trace id in the evidence note. The span names must match the code path a mentor can open.
5. Add a README section: start backend, start service, send the request, where to paste the trace id.

## Required evidence

- Committed instrumentation change in the service and committed local exporter or collector configuration
- A captured trace for a documented request containing at least two spans whose names match the code path
- The trace id recorded in the evidence note so a mentor can match the capture to the request
- README commands that start the local backend and reproduce one traced request
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Submit a repository URL plus a commit/tag reference. Do not submit only a screenshot of a flame graph with no trace id.

## Acceptance criteria

- [ ] The service contains a committed OpenTelemetry instrumentation change (SDK, auto-instrumentation, or equivalent).
- [ ] A captured trace for a documented request contains at least two spans with names that match the code path (for example handler plus outbound or datastore).
- [ ] Traces export to a local backend (collector plus UI, Jaeger, Zipkin, or a file exporter) whose configuration is committed.
- [ ] The evidence note records the trace id of that request. No paid APM product is required.

A mentor should be able to match span names to functions or routes in the repo.

## Reflection

Answer these in your own words after doing the work:

1. What can a two-span trace still hide (a missing child, a sync wait, a client timeout)?
2. Where did you decide *not* to add a span, and what would have been noisy about adding one there?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to open the handler in the repo and point at the child span without looking at the UI first.
- Do not approve a single root span with no child, or an export that only prints "tracing enabled" with no captured trace id.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes. Solution generation is not allowed for this task — wiring the exporter and choosing span boundaries yourself is the point. Any material AI assistance must be disclosed with the provider/model (if known), what it was used for, and how you verified the result.

## Completion gate

This task is complete only once the evidence is submitted and a mentor has approved a two-span trace with a recorded trace id on a local backend. LEARN BY DOING. GROW THROUGH MENTORSHIP.
