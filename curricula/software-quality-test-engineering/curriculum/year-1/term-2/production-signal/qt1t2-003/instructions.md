# Instrument Synthetic Checks as Production Test Signal

**Task ID:** `qt1t2-003`  
**Estimated effort:** 14 hours  
**Module:** Production signal

## Why this task exists

Pre-deployment tests only prove behavior at one point in time. A synthetic
check is a test that keeps running after deployment, catching failures that
only show up under real infrastructure, configuration or dependency
conditions.

This is an apprenticeship task, not a content-consumption checkbox. Hitting
`/health` every minute is not a user-facing flow.

## Authoritative resources

- **Prometheus Documentation** (reference):
  https://prometheus.io/docs/introduction/overview/

Use the official Prometheus documentation as the primary source. You may use
additional sources, but record them in your learning notes and prefer primary
documentation over tutorial aggregation sites.

## Work to complete

1. Pick a real user-facing flow on a system you control — login-then-read,
   create-then-fetch, checkout-then-confirm — not a liveness or readiness
   ping.
2. Implement a synthetic check (a scheduled job, a k6/cron probe, or a small
   worker) that exercises that flow and records success or failure.
3. Expose the result as a queryable Prometheus metric (or a push to a
   compatible gateway). Record the scrape or push interval.
4. Deliberately break the flow (stop a dependency, return 500, reject the
   payload). Capture a query or screenshot showing the metric reflecting the
   failure within one check interval.
5. Restore the flow. Capture the metric recovering.
6. Write a runbook entry: the alert threshold (a specific number or
   PromQL expression) and the first diagnostic step a person should take when
   it fires.

## Required evidence

- The synthetic check script or job configuration, committed
- The metric definition and a query/screenshot showing it during the
  deliberate failure and after recovery
- The runbook entry
- A reflection note answering the task's questions

Submit a repository URL plus the metric query output. Do not submit only a
dashboard screenshot with no interval or query text.

## Acceptance criteria

- [ ] The synthetic check exercises a real end-to-end flow, not just a
      health/ping endpoint.
- [ ] The check's result is exposed as a queryable metric with a recorded
      scrape/push interval.
- [ ] A deliberate failure is shown reflected in the metric within one check
      interval, and shown recovering after the fix.
- [ ] A runbook entry states a specific alert threshold and a first
      diagnostic step.

The mentor may break a different step in the flow and ask which metric label
or time series should move. A green `/health` scrape is not enough.

## Reflection

Answer these in your own words after doing the work:

1. What production failure would this check miss that an in-process test
   would also miss — and what would you add next to close that gap?
2. Why is the threshold you picked not "error rate > 0"?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to show the query during the failure window and name the
  interval they claimed.
- Do not approve a check that only hits a health endpoint, or a runbook that
  says "investigate" with no first step.

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
