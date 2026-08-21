# Measure First: A Repeatable Baseline Harness

**Task ID:** `pe1t1-001`
**Estimated effort:** 8 hours
**Module:** Benchmarking

## Why this task exists

Performance work that starts with a "fix" is almost always optimizing a guess. This
term starts the other way: write the success criteria, then build a harness that
can produce the same latency distribution twice. You will cite these numbers in
later tasks. A single mean from one run is not a baseline.

This is an apprenticeship task, not a reading checkbox. LEARN BY DOING. GROW
THROUGH MENTORSHIP.

## Authoritative resources

- **Prometheus Documentation** (reference): https://prometheus.io/docs/introduction/overview/
  — histogram and summary types, and why a lone average is the wrong headline.
- **OpenTelemetry Documentation** (reference): https://opentelemetry.io/docs/
  — metrics if you emit the harness timings through an SDK rather than a log file.

Use the linked documentation as the primary source. Additional sources are allowed
if you record them; prefer primary docs over tutorial aggregation sites.

## Work to complete

1. Choose a service or program you control that does work a user would wait for
   (an HTTP handler that reads or computes something, a batch job, a query
   endpoint). A static-file server or a `sleep` stub is not enough.
2. Write the SLI/SLO **before** the first timed run: a latency percentile target
   (p95 or p99, with units) and an error-rate target. Commit that file first.
3. Build a measurement harness that:
   - discards a documented warmup
   - runs a documented number of timed iterations or a documented duration
   - records **p50, p95, p99** and error rate
   - is started with **one documented command**
4. Run the harness at least three times on the same machine, without changing
   the workload between runs. Commit the raw output of each run.
5. Write a short baseline note: hardware (CPU model or cloud instance type),
   warmup count, the three p95 values, the p95 range, and a pass/fail against
   the pre-declared SLO. If it fails, say so — do not edit the SLO to match.

## Required evidence

- SLI/SLO note committed before the first results file
- Harness plus the one-command invocation
- Raw output from at least three runs (p50, p95, p99, error rate)
- Baseline note with the three p95 values and their numeric range
- Hardware and warmup note
- Reflection notes

Submit a repository URL plus an immutable commit or tag. Do not submit only a
chart without the numbers behind it.

## Acceptance criteria

- [ ] The SLI/SLO file states a p95 or p99 latency target and an error-rate
      target, and its commit precedes the first results file.
- [ ] One documented command produces a run that prints or writes p50, p95 and
      p99 — not only a mean.
- [ ] At least three run output files are committed; a variance note states the
      numeric range of p95 across those runs.
- [ ] The hardware note names the machine or instance type and the number of
      warmup iterations discarded before the timed window.

The mentor may ask why you chose that percentile and that error-rate number.
A report that only quotes average latency will be sent back.

## Reflection

Answer these in your own words after doing the work:

1. How large was the p95 range across the three runs, and what threshold would
   you treat as noise versus a real change on this machine?
2. What would a passing mean and a failing p99 tell you that the mean hides?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Check commit order: SLO file before results.
- Ask the apprentice to re-run the one command live and compare p95 to the
  committed range.
- Do not approve a mean-only headline.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the
intended path for this task. The apprentice must be able to explain, modify, run
and defend the harness. Material AI assistance must be recorded in the submission
notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after
the three-run baseline is submitted and the mentor approves the demonstrated
competency.
