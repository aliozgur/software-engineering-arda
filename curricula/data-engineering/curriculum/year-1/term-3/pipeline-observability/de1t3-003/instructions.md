# Instrument a Pipeline the Way On-Call Will Query It

**Task ID:** `de1t3-003`
**Estimated effort:** 8 hours
**Module:** Pipeline Observability

## Why this task exists

Generic process uptime is not pipeline observability. The questions are
about data movement: freshness of the last successful publish, volume
versus expectation, rejects, and how far a watermark or consumer lag
sits behind the source.

Quality shows up here as a rate you can alert on, not as a notebook of
nulls. You will also decide what pages a human and what stays silent.

## Authoritative resources

- **Python 3 Tutorial** (reference): https://docs.python.org/3/tutorial/
  — structured logging, emitting numbers you can scrape or write to a
  file.
- **PostgreSQL Documentation** (reference): https://www.postgresql.org/docs/current/
  — the queries that *are* the freshness and volume metrics if you
  compute them from the warehouse.

Use official documentation as the primary source. If you use anything else,
record it in your notes. Prometheus or a metrics file plus SQL is fine.
You do not need a full Grafana stack.

## Work to complete

1. For one real pipeline run (batch or stream), emit or query four
   metrics: freshness (time since last successful publish), volume
   (rows or events in the run), error or reject count, and lag or
   watermark delay. Capture the values.
2. Emit structured logs with a `run_id` on every task or stage of that
   run. Submit at least four lines that share the same id.
3. Write an alert-policy note: one condition that pages (for example
   freshness above N minutes) and one that must not page (for example
   a single-row reject while volume is inside band). Both thresholds
   are numbers.
4. Answer two operational questions with a query or command and
   captured output: "is the named 09:00 (or fixture-clock) load late?"
   and "did we drop more than 1% of rows?"
5. Do not submit host CPU as a substitute metric. If you also have
   process metrics, they are extra, not a replacement.

## Required evidence

- Captured values from one real run for the four metrics
- At least four structured log lines from that run sharing one
  `run_id`
- An alert-policy note with one paging threshold and one non-paging
  threshold, both numeric
- Two operational queries or commands with captured output
- Reflection notes answering the questions below

Submit a repository URL plus a commit reference for the instrumentation
code.

## Acceptance criteria

- [ ] Four named metrics exist with captured values from a real run:
      freshness, volume, error or reject count, and lag or watermark
      delay.
- [ ] Every submitted log line from one run shares one `run_id`, and at
      least four such lines are included.
- [ ] The alert-policy note states one paging condition and one
      non-paging condition, each with a numeric threshold.
- [ ] Two operational questions — whether a named load is late, and
      whether drop rate exceeded one percent — have a query or command
      and captured output.

The mentor may ask a third on-call question live. If the four metrics
cannot answer it and you cannot say which field is missing, the schema
is incomplete.

## Reflection

Answer these in your own words after doing the work:

1. Which of the four metrics would you page on first, and which would
   you never page on alone?
2. What drop-rate definition did you use (rejects / extracted, or
   something else), and what does that definition hide?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you learned the objective?

## Mentor review guide

Ask the apprentice to answer "are we late?" using only the captured
metrics and logs, no application debugger. Do not approve a dashboard
screenshot with no numbers you can recompute.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is
not the intended path for this task. The apprentice must compute
freshness and drop rate without the model. Material AI assistance must
be recorded in the submission notes with the provider/model (if known),
purpose, and verification performed.

## Completion gate

This task is not complete when logs exist. It is complete once the four
metrics, the `run_id` chain, the two alert thresholds, and the two
operational answers are submitted and the mentor approves the
demonstrated competency.
