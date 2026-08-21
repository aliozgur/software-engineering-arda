# Diagnose a Performance Regression Under Realistic Load

**Task ID:** `qt1t2-004`  
**Estimated effort:** 18 hours  
**Module:** Performance diagnosis

## Why this task exists

Optimizing the wrong thing costs time and adds complexity with no benefit.
This task is deliberately open-ended: nobody hands you the bottleneck up
front in production.

This is an apprenticeship task, not a content-consumption checkbox. A
premature cache or a guessed index is not a diagnosis.

## Authoritative resources

- **k6 Documentation** (reference): https://k6.io/docs/
- **Prometheus Documentation** (reference):
  https://prometheus.io/docs/introduction/overview/

Use the official documentation as the primary source. You may use additional
sources, but record them in your learning notes and prefer primary
documentation over tutorial aggregation sites.

## Work to complete

1. Start from a system that behaves worse than expected under the workload
   from `qt1t2-001` (or an equivalent load test). If the system already meets
   its SLO easily, introduce a realistic bottleneck you will later diagnose
   from measurements — an N+1 query, a lock, a synchronous remote call, an
   unbounded scan — then treat the measurements as the source of truth, not
   your memory of what you planted.
2. Write a bottleneck hypothesis *before* you implement a fix. Include at
   least one hypothesis you later reject, and why the evidence killed it.
3. Gather profiling or metrics evidence that supports the hypothesis you
   keep: a profile, a PromQL query, an explain plan, lock traces. An
   assumption without a measurement does not count.
4. Apply one fix aimed at that bottleneck. Re-run the identical workload and
   report before/after latency distributions (p95 or p99, not only the mean).
5. Run the correctness test suite after the fix and capture it passing. A
   faster system that is now wrong is a failed task.

## Required evidence

- Profiling or metrics output supporting the identified bottleneck
- A written hypothesis recorded before the fix, including any hypothesis that
  turned out wrong
- Before/after load test results for the identical workload
- A correctness test suite run showing it still passes after the fix
- A reflection note answering the task's questions

Submit a repository URL plus the measurement artifacts. Do not submit only
"I added a cache and it got faster."

## Acceptance criteria

- [ ] A specific bottleneck hypothesis is recorded in writing before the fix
      is implemented.
- [ ] Profiling or metrics evidence supports the identified bottleneck, not
      just an assumption.
- [ ] Before/after latency distributions for the identical workload are both
      reported.
- [ ] The correctness test suite is shown passing after the performance fix.

The mentor may ask you to defend the rejected hypothesis and the measurement
that killed it. A faster mean with no distribution and no correctness run is
not enough.

## Reflection

Answer these in your own words after doing the work:

1. Which hypothesis did you believe first, and what measurement forced you
   to drop it?
2. What did you refuse to optimize, and what evidence said it was not the
   bottleneck?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to point at the measurement that names the bottleneck
  before they open the fixing commit.
- Do not approve a fix committed before the hypothesis note, or a speedup
  with no correctness suite run.

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
