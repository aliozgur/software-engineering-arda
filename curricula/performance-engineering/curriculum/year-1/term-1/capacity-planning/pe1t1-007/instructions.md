# Capacity From Your Own Numbers

**Task ID:** `pe1t1-007`
**Estimated effort:** 10 hours
**Module:** Capacity planning

## Why this task exists

`sa1t2-002` builds a back-of-envelope model whose inputs can be assumed. That
is the right exercise when you have no system yet. You have a system, a
harness, and a knee. This task is the audit: **every input cites a run**. If
you cannot point at a file for an RPS or p95, you may not use that number.

## Authoritative resources

- **Prometheus Documentation** (reference): https://prometheus.io/docs/introduction/overview/
  — rate and histogram queries if you pull SLO-meeting RPS from a scrape
  rather than from the load-generator log.
- **MIT 6.006 - Introduction to Algorithms** (reference):
  https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-fall-2011/
  — growth: if per-request work is linear in input size, a 5x traffic
  projection that also grows payload size is not 5x CPU.

## Work to complete

1. Open `pe1t1-006`. Copy into a capacity note:
   - SLO-meeting offered load (the sub-knee operating point, not the knee)
   - p95 and error rate at that point (use the three-run range; state which
     statistic you treat as the planning number)
   - the saturation signal and its value at the knee
   Each line must cite a **file path or run id** in the repository.
2. If a number is missing, **re-run** the load command and commit the new
   output here. Do not invent a tidy figure.
3. Choose a peak of **at least 2×** the SLO-meeting load (you may pick a
   business peak if you still show the 2× floor). Write the formula for
   required replicas or equivalent capacity, including headroom you choose
   (and why). Show the arithmetic. The output is an integer you would order
   or configure, plus the leftover fraction.
4. Project **2×** and **5×** the SLO-meeting load. For each, name the
   resource that hits a **stated limit** first (for example max connections,
   a CPU percent you measured per RPS, or queue depth). The per-request or
   per-second cost must come from a measurement already in the repo.
5. Sensitivity: take one cited input, multiply by 2 or by 0.5, and recompute
   the replica/capacity number with the same formula. State whether the
   conclusion changes.

## Required evidence

- Capacity note with cited inputs
- Written formula and arithmetic for ≥ 2× peak
- 2× and 5× projections with the first-limit resource and its measured cost
- Sensitivity recompute
- Reflection notes

## Acceptance criteria

- [ ] Every input number in the capacity note cites a committed run file or
      log line from `pe1t1-006` or a re-run in this task — no invented RPS
      or p95.
- [ ] Required capacity for a peak of at least 2× the measured SLO-meeting
      load is computed with the formula written out (not only the final
      integer).
- [ ] The 2× and 5× projections each name one resource and the measured
      per-request or per-second cost that makes that resource the first
      limit.
- [ ] The sensitivity case changes one cited input by 2× or 0.5× and shows
      the new capacity number from the same formula.

The mentor will change one cited input live. If you cannot recompute in a
few minutes, the note is a narrative, not a model.

## Reflection

Answer these in your own words after doing the work:

1. Which cited input, if wrong by 2×, moves the replica count the most, and
   what is the new number?
2. What would you refuse to put in a capacity review that the architecture
   back-of-envelope task would have allowed?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Change the headroom fraction or the SLO-meeting RPS and ask for a live
  recompute.
- Reject any input that cannot be opened as a file in the repo.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may explain utilization and headroom and quiz the formulas. It must not
supply the capacity numbers for your runs. Disclose material AI assistance
with provider/model, purpose, and verification performed.

## Completion gate

Complete only after the cited-input note, the shown arithmetic, and the
sensitivity recompute are submitted and the mentor approves.
