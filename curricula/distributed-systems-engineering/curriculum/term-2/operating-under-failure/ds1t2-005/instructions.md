# Traces That Distinguish Refuse, Hang, and Accepted-then-Lost

**Task ID:** `ds1t2-005`
**Estimated effort:** 16 hours
**Module:** Operating Under Failure

## Objective

Put OpenTelemetry on a path you already operate: the replicated or
partitioned store, the outbox-to-Kafka pipeline, or both. Inject three
failures that produce three different client-visible outcomes — **refuse**
(error returned), **hang** (no timely response), **accepted-then-lost**
(client got success, the write or event is gone). Export the traces. Write
a decision table that classifies a request from telemetry alone, then
score that table on 30 labeled requests.

## Why this task exists

Terms 1 and 2 have been about making anomalies appear. An on-call
engineer does not get your injector log. They get spans, maybe metrics.
If those signals cannot tell "we said no" from "we said yes and then
dropped it," the availability contract from `ds1t1-002` is not operable.
This is the first task whose primary artifact is a classification rule,
not a new subsystem.

## Authoritative resources

- **OpenTelemetry Documentation** (primary): https://opentelemetry.io/docs/
  — traces, spans, status, attributes, context propagation, and an
  exporter you can dump to JSON (OTLP collector, file exporter, or
  console with a captured run).
- **Docker Get Started** (reference): https://docs.docker.com/get-started/
  — optional collector / backend in Compose.

## Setup notes

- Reuse an existing system. Do not start a toy "hello span" service
  unless it still fronts the store or the outbox path.
- A GUI screenshot is not enough. Export spans as JSON (or protobuf
  decoded to text) so a mentor can grep request ids.
- Metrics are welcome (request count, error count, consume lag) but the
  decision table must be usable from traces; metrics may only break ties.
- "Hang" means the client hits a timeout you configured, and the server
  span is missing or never ends. Do not fake a hang with a sleep that
  still returns 200.

## Work to complete

1. Instrument the client, the receiving service, and at least one
   downstream hop (follower RPC, outbox poller, or Kafka produce) with
   a shared `request_id` / `order_id` attribute and propagated context.
2. Build three injector modes, deterministic:
   - **Refuse:** partition or fence so the service returns an error
     (4xx/5xx, or your store's explicit refuse) and the trace is
     complete with an error status.
   - **Hang:** pause or black-hole the handler so the client times out;
     the server span is absent or unterminated at timeout.
   - **Accepted-then-lost:** the dual-write kill, an unclean-election
     loss, or a relaxed read of a never-replicated write — client span
     is OK; a later consume or quorum read for that id finds nothing.
3. Export one worked-example trace for each mode. Label the files.
4. Write a decision table: columns for span graph shape, status, duration
   vs client timeout, presence/absence of a named child span. Rows for
   the three outcomes. No row may say "because we killed X."
5. Run at least 30 injected requests in shuffled order. For each, assign
   a label using **only** the table and the exported telemetry. Then
   compare to the injector's true class. Record 24/30 or better. Explain
   every mismatch — if the table is wrong, fix the table and rerun, or
   keep the score and say why the leftover cases are indistinguishable.
6. `README.md` includes the table, the timeout number, and the score.

## Evidence you'll submit

- Instrumentation commits (client, service, downstream).
- Three labeled exported traces.
- Decision table and the 30-request score sheet (assigned vs true).
- Reflection notes.

## Acceptance criteria

- [ ] Each of the three outcomes has an exported trace (or trace +
      metrics) that a second person can open without the injector logs.
- [ ] The decision table uses only telemetry fields (span status, span
      name, duration, missing child span, attribute values) — not "we
      killed the leader."
- [ ] The 30-request labeling run uses the table alone and records both
      the assigned label and the injector's true class; at least 24 of
      30 match, and every mismatch is explained.
- [ ] Accepted-then-lost is not labeled as refuse: the client or service
      span must have recorded success while a downstream span is missing
      or a consume/read span never appears for that request id.

## Reflection

Answer in your own words after doing the work:

1. Which of the three outcomes was hardest to tell from refuse, and
   which span had to exist (or not exist) before you trusted the label?
2. If you could add only one metric to the table, which would it be, and
   which mismatch would it have fixed?

Also record: what took longer than expected, and what remains unclear
about "the request succeeded" as a sentence a client and a replica would
both sign.

## Mentor review guide

If a mentor reviews this work, hide the injector logs and hand the
apprentice a fourth exported trace they have not labeled. Do not approve
a table that mentions SIGSTOP or `kill` as a feature. Do not approve
screenshots without JSON.

Suggested review outcome: **Approve**, **Request revision**, or **Create
follow-up challenge**.

## AI use policy

Mode: **guided**. Explain, hint, and quiz are available; solution
generation is not — including not generating the 30 labels from the
injector file. Disclose any material AI use with provider/model,
purpose, and verification performed.

## Completion gate

This task is complete only after the evidence is submitted and, when a
mentor is present, the mentor approves the demonstrated competency.
Instrumentation without the score sheet is not complete.
