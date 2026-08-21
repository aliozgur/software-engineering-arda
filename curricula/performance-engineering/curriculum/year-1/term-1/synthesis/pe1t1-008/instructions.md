# One Evidenced Win, One Rejected Fake

**Task ID:** `pe1t1-008`
**Estimated effort:** 12 hours
**Module:** Synthesis

## Why this task exists

You have spent the term refusing to guess. This close is where a change is
finally allowed — once. The software-engineering task `y3t2-004` asks for an
improvement and a rejected optimization in the same breath as the first
baseline. You already own the baseline, the profiles, the traces, the plans,
and the knee. The question now is judgment: **one win with numbers**, and
**one fake win you refuse to ship**.

LEARN BY DOING. GROW THROUGH MENTORSHIP.

## Authoritative resources

Use the same primary docs you have been citing; pick the one that matches
the bottleneck you actually found:

- **Prometheus Documentation**: https://prometheus.io/docs/introduction/overview/
- **OpenTelemetry Documentation**: https://opentelemetry.io/docs/
- **PostgreSQL Documentation**: https://www.postgresql.org/docs/current/
- **MIT 6.006**: https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-fall-2011/

## Work to complete

1. Write and commit a **hypothesis** before any optimization commit: the
   bottleneck (function, span, plan node, or saturated resource) and the
   metric you expect to move (`p95` or SLO-meeting RPS). Point at an
   existing artifact (`pe1t1-002` frame, `pe1t1-003` span, `pe1t1-005`
   plan, or `pe1t1-006` saturation).
2. Capture a **before** run with the identical `pe1t1-001` harness command
   or the `pe1t1-006` sub-knee command. Quote p95 or SLO-meeting RPS.
3. Implement **one** change aimed at that bottleneck. Re-run the **same**
   command. The metric must move in the intended direction. Compute the
   delta. If it does not move, that change becomes your rejected fake and
   you try a different change for the win — still hypothesis-first.
4. Implement (or reuse an earlier experiment from `pe1t1-004` / `pe1t1-005`)
   a **second** change that looked plausible. Measure it on the same
   command. Document no gain or a regression. Leave it **off** the default
   path (reverted, flagged off, or never merged to the running config).
5. Revalidate **correctness**: run the existing tests or a recorded
   invariant (row counts, checksum, cache-after-write case). Show a passing
   result after the shipped change.

## Required evidence

- Hypothesis file committed before the optimization diff
- Before and after outputs, same command, with p95 or SLO-meeting RPS
- Shipped-change note: numeric delta plus the earlier artifact that
  justified the change
- Rejected-change note: before/after numbers, not on the default path
- Passing correctness test or invariant after the shipped change
- Reflection notes

## Acceptance criteria

- [ ] The hypothesis file is committed before the first optimization commit
      and names one bottleneck plus one metric (p95 or SLO-meeting RPS).
- [ ] Before and after runs use the same documented command; both results
      quote p95 or SLO-meeting RPS as numbers.
- [ ] The shipped change moves that metric in the intended direction; the
      delta is computed from the two runs.
- [ ] A second change has committed before/after numbers showing no gain or
      a regression and is absent from the default path.
- [ ] A correctness test or recorded invariant is shown passing after the
      shipped change.

The mentor may change the workload shape (payload size, key reuse, or
concurrency). If the "win" vanishes and you cannot explain why from a
profile or plan, the win was fitted to one run.

## Reflection

Answer these in your own words after doing the work:

1. What made the rejected change look like a win before you measured it,
   and which number killed it?
2. After the shipped change, what is the next bottleneck, and which
   existing artifact already points at it?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Change workload shape and ask whether the shipped optimization still
  helps. The apprentice should predict from profile/plan/trace, then run.
- Do not approve a rejected-change note that has no numbers.
- Do not approve a missing correctness check.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may explain techniques and quiz you on how you would verify a delta. It
must not generate the optimization or the before/after numbers. Disclose
material AI assistance with provider/model, purpose, and verification
performed.

## Completion gate

Complete only after the hypothesis, the numbered win, the numbered reject,
and the correctness check are submitted and the mentor approves.
