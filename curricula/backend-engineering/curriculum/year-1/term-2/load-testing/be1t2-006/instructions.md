# Load Test the Service and Name the Bottleneck

**Task ID:** `be1t2-006`
**Estimated effort:** 14 hours
**Module:** Load Testing

## Why this task exists

You have indexes and metrics. You do not yet know what breaks first
when many callers arrive at once. This task asks for a repeatable
load script, two runs with the same parameters, and a bottleneck
named from evidence — not from intuition.

## Authoritative resources

- **Python 3 Tutorial** (reference): https://docs.python.org/3/tutorial/
- **Prometheus Documentation** (reference): https://prometheus.io/docs/introduction/overview/

A small Python script, `hey`, `wrk`, or `k6` are all acceptable. The
script must be committed and rerunnable. Use the metrics you added
in the previous task as one of the evidence sources for the
bottleneck.

## Work to complete

1. Write a load script against the *containerized* service, hitting
   at least one authenticated read path and one write path. Document
   how test credentials are supplied.
2. Define the offered load in writing before you run it (duration
   and either requests per second or concurrent callers). Commit
   that definition with the script.
3. Run the baseline. Record p50, p95, p99, error rate, duration, and
   offered load. Commit the report as a file.
4. While the baseline is running, collect at least one supporting
   signal: an `EXPLAIN ANALYZE` of a hot query, a `/metrics` scrape,
   or a profiler/output showing where time went.
5. Name the bottleneck in a short note that points at that signal.
   Make *one* change aimed at it (an index, a query rewrite, a pool
   size, a cache with a documented invalidation rule).
6. Rerun the *same* script with the *same* parameters. Commit the
   second report. Do not retune the load to make the second run look
   better.

The git history should read: script and load definition → baseline
report → the one change → second report. A single commit that
contains both reports is not process evidence.

## Required evidence

- The committed load script and the exact command line used for
  both runs
- Two run reports (baseline and after the change) each listing p50,
  p95, p99, error rate, duration, and offered load
- A bottleneck note that points at a specific file, query plan, or
  metric sample — not a guess
- The single change made after the baseline, as its own commit
- Git history showing script, baseline report, change, then second
  report, in that order

Submit a repository URL plus a commit reference. Do not submit only
a screenshot of a terminal.

## Acceptance criteria

- [ ] The load script is committed and the README names the exact
      command to rerun it against the containerized service.
- [ ] Both committed reports list p50, p95, p99, error rate,
      duration, and the offered load (requests per second or
      concurrent callers).
- [ ] The bottleneck note cites a specific file, `EXPLAIN` plan, or
      metric sample collected during the baseline run.
- [ ] The second run uses the same script and the same load
      parameters as the first.

The mentor may rerun the script from the README and compare their
shape of results to yours. Absolute numbers will differ by machine;
missing fields or a different command will not pass.

## Reflection

Answer these in your own words after doing the work:

1. What did the baseline reports say that your metrics did not, or
   the other way around?
2. Why was the one change the right first change, and what did you
   refuse to change?
3. At what offered load would you call this service over capacity?

Also record:

- What took longer than expected?
- What would you include in the next load run?
- What remains unclear?

## Mentor review guide

- Confirm both reports share the same command and load parameters.
- Open the bottleneck note and follow the citation to a real file
  or scrape.
- Reject a second run that quietly lowered concurrency or duration.

Suggested review outcome: **Approve**, **Request revision**, or
**Create follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes.
Solution generation is not the intended path for this task. Material
AI assistance must be disclosed with the provider/model (if known),
purpose, and verification performed.

## Completion gate

This task is complete only once the evidence is submitted and the
mentor approves the demonstrated comparison — not when a load tool
has been run once.
