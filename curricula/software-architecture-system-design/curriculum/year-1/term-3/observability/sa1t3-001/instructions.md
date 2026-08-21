# Observability as an Architectural Surface

**Task ID:** `sa1t3-001`
**Estimated effort:** 8 hours
**Module:** Observability

## Why this task exists

Term 3 starts by asking whether last term's design can be operated. SLOs
without signals are decorations. This task is not an instrumentation
implementation: it is a design review of what you would need to see at each
boundary, and what you are willing to drop when cardinality or sampling cost
shows up. An architect who cannot say which span, metric, or log event would
distinguish two failures has not finished the design.

Reading OpenTelemetry concepts is preparation. Completion requires a map, two
diagnoses that use only that map, and a limit you can defend.

## Authoritative resources

- **OpenTelemetry Documentation** (primary): https://opentelemetry.io/docs/ —
  read the signals overview (traces, metrics, logs) and enough about sampling
  to write a limit as a number, not as "we'll sample some of it."

Use official documentation as the primary source. If you use other material,
record it in your notes.

## Work to complete

1. Take a service-boundary diagram from a prior task (`sa1t2-001`,
   `sa1t2-004`, or a mentor-assigned equivalent). Every arrow that crosses a
   process or trust boundary is in scope.
2. For each boundary, name at least one signal — a span, a metric, or a log
   event — and the question it answers (for example: "did the payment capture
   start, and how long did it take?"). Prefer the cheapest signal that answers
   the question; do not put a trace on every row by default.
3. Write two distinct failure scenarios (timeout on one dependency, wrong
   result from another, a retry storm, a stale cache). Diagnose each using
   only the signals on the map. Name the specific signal that distinguishes
   the two causes. If you cannot distinguish them, add the missing signal and
   say why it was missing on the first pass.
4. Write an ADR for a sampling rate or a cardinality limit (for example:
   trace 1 in 100 of successful reads; cap a label at 50 values). Name the
   diagnosis that is lost or delayed when that limit is hit.

## Required evidence

- An instrumentation map covering every service boundary on a prior diagram,
  each with at least one named signal and the question that signal answers
- A diagnosis note for two distinct failure scenarios that uses only the named
  signals and states which signal distinguishes the cause
- An ADR stating a sampling rate or a cardinality limit as a number, and naming
  the diagnosis that is lost when that limit is hit

Submit a repository URL plus a commit reference. Commit the first map and the
revised map separately if a missing signal was added after the diagnosis
attempt.

## Acceptance criteria

- [ ] Every service boundary on the submitted diagram has at least one named
      signal and a question that signal is meant to answer.
- [ ] Each of two failure scenarios is diagnosed using only the named signals,
      and the note names the specific signal that distinguishes the cause from
      the other scenario.
- [ ] The ADR states a sampling rate or cardinality limit as a number and names
      one diagnosis that becomes impossible or delayed when that limit is hit.

## Reflection

1. Which boundary had no honest signal on the first pass, and what question
   were you hoping "the logs" would answer without naming an event?
2. If you had to cut the instrumentation budget in half, which signal would
   you drop, and which of the two failures would you then be unable to
   distinguish?

Also record: what took longer than expected, what you'd practice again, what
remains unclear.

## Mentor review guide

- Invent a third failure that looks like one of the two on the happy-path
  metrics. Ask which named signal would tell them apart. If the answer is a
  new signal not on the map, request revision.
- Do not approve a map that assigns "distributed trace" to every boundary
  with the same question.

Suggested outcome: **Approve**, **Request revision**, or **Discuss live**.

## AI use policy

Mode: **guided**. AI may explain OpenTelemetry signals and quiz your
understanding of sampling and cardinality. AI must not produce the map or the
diagnoses for your specific boundaries. Disclose any material AI use.

## Completion gate

This task is not complete when every box has a telemetry sticker. It is
complete once two failures are distinguishable from the named signals alone,
and you can state what diagnosis the sampling limit gives up.
