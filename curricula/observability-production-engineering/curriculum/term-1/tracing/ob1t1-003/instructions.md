# Distributed Tracing Across Real Service Calls

**Task ID:** `ob1t1-003`
**Estimated effort:** 10 hours
**Module:** Tracing

## Why this task exists

A single-process log or metric can't show you where time actually goes once a request
crosses a network boundary. This task requires a real trace across at least two
independently-running processes, and requires you to diagnose a problem using only the
trace — not by reading the code that caused it.

## Authoritative resources

- **OpenTelemetry Documentation** (reference): https://opentelemetry.io/docs/ — read the
  tracing concepts (spans, context propagation, exporters) before instrumenting.

## Work to complete

1. Stand up, or reuse, at least two independently-running components that participate in
   one logical request — two HTTP services, or one service plus a datastore/queue call you
   wrap in its own span. Reusing the service from `ob1t1-001` / `ob1t1-002` is expected.
2. Instrument the request path end-to-end: a root span at the entry point, child spans for
   each downstream call, and context propagation carrying the same trace id across the
   process boundary (not restarting a new trace per process).
3. Export the trace to something you can inspect — Jaeger, Zipkin, a console exporter, or
   any OTel-compatible backend — and capture the baseline trace.
4. Inject a deliberate delay into one specific downstream span (a sleep, an artificial
   wait, or a genuinely inefficient operation) and capture a second trace.
5. Write a short diagnosis note identifying which span accounts for the added latency and
   how you knew that from the trace data alone — span names and durations, not source code.

## Required evidence

- Baseline trace export/screenshot with the trace id visible across both process/service
  labels
- Instrumentation code/config showing the propagation mechanism
- Second (slowed) trace export/screenshot
- Diagnosis note
- Reflection notes

## Acceptance criteria

- [ ] The exported baseline trace shows a single trace id shared by spans from both
      processes.
- [ ] The trace has a parent/child span structure reflecting the real call order.
- [ ] The second trace's longest span corresponds to the component deliberately slowed
      down.
- [ ] The diagnosis note identifies the slow span using only span names/durations, not
      source-code inspection.

The mentor may hide which component was slowed down and ask the apprentice to find it
live from the trace only. If you are working without a mentor, have a script pick which
downstream call to slow, capture the trace, and write the diagnosis before opening the
injector output that names the chosen component.

## Reflection

1. What would this incident look like as three separate service logs instead of one
   trace — what question becomes harder, or impossible, to answer?
2. Where would you add one more span if you had another hour, and what would it let you
   see that you can't see now?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you learned the objective?

## Mentor review guide

Mentorship is optional. When a mentor is present: swap which downstream call is slowed
and ask the apprentice to re-diagnose live from a fresh trace, without re-reading their
own code first.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the intended
path for this task. Material AI assistance must be recorded in the submission notes with
provider/model (if known), purpose, and verification performed.

## Completion gate

Complete only once the second trace demonstrably localizes the injected delay and the
demonstrated competency is approved.
