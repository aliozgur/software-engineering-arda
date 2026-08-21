# Add a Performance Regression Gate to the Pipeline

**Task ID:** `qt1t2-002`  
**Estimated effort:** 16 hours  
**Module:** Performance CI

## Why this task exists

A load test that only runs manually before a big release catches regressions
too late and too rarely. A gate in the pipeline catches them at the commit
that introduced them.

This is an apprenticeship task, not a content-consumption checkbox. A CI job
that runs k6 and always exits zero is not a gate.

## Authoritative resources

- **k6 Documentation** (primary): https://k6.io/docs/
- **GitHub Actions Documentation** (reference): https://docs.github.com/actions
- **GitLab CI/CD Documentation** (reference): https://docs.gitlab.com/ci/

Pick whichever CI platform hosts your repository. Use the official documentation
as the primary source; if you use other material, record it in your notes and
prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Reuse the load test and SLO from `qt1t2-001` (or an equivalent committed
   baseline). Store the baseline as an artifact the pipeline can read — a
   committed JSON file, an uploaded previous-run summary — not a number you
   type into the job on the day of the demo.
2. Add a CI job that runs the load test and fails when latency or error rate
   regresses beyond a stated margin against that baseline.
3. Document how you handle CI noise: the specific margin, iteration count, or
   comparison rule, and why that number is large enough to absorb variance
   from `qt1t2-001` without hiding a real regression.
4. Introduce a deliberate regression (an artificial sleep, a worse algorithm,
   a tighter loop). Capture the pipeline failing with the comparison output.
5. Revert the regression. Capture the pipeline passing again.

## Required evidence

- The CI job configuration for the performance gate
- Pipeline log or output showing the gate failing on a deliberate regression
- Pipeline log or output showing the gate passing after the regression is
  reverted
- A written note on how CI noise/variance was accounted for

Submit a repository URL plus pipeline logs. Do not submit only a green check
on a job that never compared to a baseline.

## Acceptance criteria

- [ ] The CI configuration runs the load test and compares the result to a
      stored baseline, not an arbitrary hardcoded number picked without
      justification.
- [ ] A deliberately introduced regression is shown failing the gate, with the
      pipeline output captured.
- [ ] The pipeline is shown passing again once the regression is reverted.
- [ ] The noise/variance-handling approach is documented, naming the specific
      margin or iteration count chosen.

The mentor may ask what size regression would still slip under your margin.
A hardcoded `p95 < 500ms` with no baseline file is not enough unless you
justify that number from prior measurements and treat it as the stored
baseline.

## Reflection

Answer these in your own words after doing the work:

1. What regression size would your margin still accept, and is that acceptable
   for this API?
2. What did you change about the workload or the runner so CI results are
   comparable to the local baseline?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to point at the baseline file and the comparison line in
  the failing log, and to name the margin used.
- Do not approve a job that runs k6 without failing on a worse result.

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
