# Attribute Latency With Traces, Not Averages

**Task ID:** `pe1t1-003`
**Estimated effort:** 10 hours
**Module:** Profiling

## Why this task exists

The CPU profile from `pe1t1-002` answers "what burned the core." This task
answers "where the user waited." Those are different questions. A request that
spends 80 ms in a database round-trip can have a quiet CPU profile and a bad
p95. You will instrument one path, capture a fast trace and a slow trace, and
say whether wall time and CPU time agree.

## Authoritative resources

- **OpenTelemetry Documentation** (primary): https://opentelemetry.io/docs/
  — traces, spans, context propagation, and how to export a single trace.
- **Prometheus Documentation** (reference): https://prometheus.io/docs/introduction/overview/
  — if you also expose a latency histogram for the same operation, use it to
  pick a slow request rather than guessing which one looked slow.

## Work to complete

1. Instrument the same operation you measured in `pe1t1-001` / `pe1t1-002` with
   OpenTelemetry (or an equivalent that exports OTLP/JSON). One **parent** span
   for the request, and **at least three named child spans** on that path
   (examples: parse, store read, compute, serialize — names that match your
   code, not generic `span1`).
2. Drive the harness. Export **one fast request** and **one slow request** for
   the same operation. Commit the trace exports (JSON, OTLP dump, Jaeger/Zipkin
   export). Each span must have a duration in milliseconds you can quote.
3. Compute, from those milliseconds, which child consumed the largest share of
   the slow parent's duration. Write that share as a percentage.
4. Open the `pe1t1-002` diagnosis (or re-take a short CPU profile here). State
   whether the largest latency span is the same work as the hottest CPU frame.
   If they disagree, name the difference (waiting vs computing, another
   process, lock, I/O). Do not "fix" the path in this task.

## Required evidence

- Instrumentation producing a parent span and at least three named children
- Fast-request trace export with millisecond durations
- Slow-request trace export with millisecond durations
- Comparison note: largest child share as a percentage, plus match/mismatch
  with the `pe1t1-002` hot frame
- Reflection notes

A screenshot of a trace UI is allowed only if the same numbers appear in a
committed export or a pasted JSON excerpt in the note.

## Acceptance criteria

- [ ] A captured trace for one request includes a parent span and at least
      three distinctly named child spans.
- [ ] Fast and slow traces for the same operation are both committed, each
      listing span durations in milliseconds.
- [ ] The comparison note computes the largest child span's share of the slow
      parent duration as a percentage from those milliseconds.
- [ ] The note states match or mismatch with the hottest CPU frame from
      `pe1t1-002` (or a re-taken profile in this task) and names the difference
      if they disagree.

The mentor may pick a span and ask what code it wraps. If you cannot point at
the instrumentation site, the traces are decoration.

## Reflection

Answer these in your own words after doing the work:

1. If the largest latency span was **not** the hottest CPU frame, what was the
   process waiting on, and which span duration is the evidence?
2. Which span would you delete first if you had to cut instrumentation cost,
   and what decision would you lose?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to walk a third, unseen request in the exporter and name
  the largest child without looking at their note.
- If CPU and traces agree, ask what workload shape would make them diverge.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may explain span APIs and quiz you on parent/child relationships. It must
not invent span timings for a request you did not run. Disclose material AI
assistance with provider/model, purpose, and verification performed.

## Completion gate

Complete only after both traces and the comparison with the CPU profile are
submitted and the mentor approves the attribution.
