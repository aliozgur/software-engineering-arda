# Establish a Load-Testing Baseline and SLO

**Task ID:** `qt1t2-001`  
**Estimated effort:** 14 hours  
**Module:** Load testing

## Why this task exists

Performance work without a repeatable baseline is guesswork: you cannot tell a
real regression from noise, and you cannot tell an improvement from a fluke.

This is an apprenticeship task, not a content-consumption checkbox. One k6 run
with a mean latency is not a baseline.

## Authoritative resources

- **k6 Documentation** (primary): https://k6.io/docs/

Use the official k6 documentation as the primary source. You may use additional
sources, but record them in your learning notes and prefer primary documentation
over tutorial aggregation sites.

## Work to complete

1. Pick a real HTTP API you control (or can run locally). A single static file
   server is not enough; the endpoint must do some work a user would wait for.
2. Write the SLO *before* you look at load-test results: a latency percentile
   target (p95 or p99) and an error-rate target. Commit that statement first.
3. Write a k6 script that applies a documented workload shape (virtual users,
   duration, and think time or arrival rate). One command must produce that
   same shape every run.
4. Run the script at least three times on comparable hardware. Record p95 or
   p99 latency, error rate, and run-to-run variance for each run. Do not
   report only the mean.
5. Write a short report: the pre-declared SLO, the measured distribution, the
   variance, and a pass/fail verdict against the SLO. If it fails, say so —
   do not quietly loosen the SLO to match the data.

## Required evidence

- The load test script, committed to the repository
- Raw output or a report from at least 3 runs
- A short report stating the SLO, the measured latency distribution, and a
  pass/fail verdict
- A reflection note answering the task's questions

Submit a repository URL plus the raw k6 output. Do not submit only a chart
without the numbers.

## Acceptance criteria

- [ ] The SLO (a latency percentile target and an error-rate target) is stated
      before results are shown, not fitted to them afterward.
- [ ] The load test runs with a single documented command and produces the same
      workload shape each run.
- [ ] Results from at least 3 runs are reported, including run-to-run variance.
- [ ] The verdict against the SLO cites p95 or p99 latency, not only the mean.

The mentor may ask why you chose that percentile and that error-rate number.
A single run that "looks fine" is not a baseline.

## Reflection

Answer these in your own words after doing the work:

1. How much of the run-to-run variance would you treat as noise versus a real
   change, and what number did you use to decide?
2. What would a passing mean and a failing p99 tell you that the mean alone
   hides?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask whether the SLO was written before or after the first run, and check the
  commit order.
- Do not approve a report that only quotes average latency.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the
intended path for this task. The apprentice must be able to explain, modify, test
and defend every submitted artifact. Material AI assistance must be recorded in the
submission notes with the provider/model (if known), purpose, and verification
performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the
evidence is submitted and the mentor approves the demonstrated competency.
