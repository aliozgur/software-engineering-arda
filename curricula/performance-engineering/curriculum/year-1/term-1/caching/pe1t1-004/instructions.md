# Cache Only With Evidence

**Task ID:** `pe1t1-004`
**Estimated effort:** 10 hours
**Module:** Caching

## Why this task exists

Adding a cache because "reads are probably hot" is the same guess this term
banned in `pe1t1-002`. You will measure the uncached path, add a cache only
after you have a miss-cost number, and keep the cache only if the harness
shows a p95 (or hit-rate) change you can quote. You will also write the
invalidation rule and watch one correctness case — a cache that lies after a
write is not a performance win.

## Authoritative resources

- **PostgreSQL Documentation** (reference): https://www.postgresql.org/docs/current/
  — use this when the origin of truth is a query; caching a result does not
  replace understanding what the planner already does (see also `pe1t1-005`).
- **MIT 6.006 - Introduction to Algorithms** (reference):
  https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-fall-2011/
  — hash-table expected cost vs scanning the origin on every miss.

## Work to complete

1. Pick a read path whose origin is a real store (PostgreSQL is the default;
   another durable store is acceptable if you say why). Drive it with the
   `pe1t1-001` harness or the same command documented here.
2. Run and commit a **no-cache baseline**: p50/p95/p99 for that command. Quote
   the miss cost as the measured p95 (or the origin span time from
   `pe1t1-003` if you still have traces).
3. Add a cache (in-process, Redis, or query-result table — your choice) with
   **hit and miss counters** you increment in code. Do not estimate hit rate.
4. Re-run the **identical** workload command. Report hit rate as
   `hits / (hits + misses)` from those counters, after-cache p95, and the
   delta vs baseline. If p95 does not move, say so and either change the
   workload so the cache is exercisable or document the cache as a failed
   experiment — do not invent a win.
5. Write the invalidation or TTL rule: which write or expiry clears which key.
   Perform one correctness case (update the origin, then read) and record
   whether the reader saw fresh data, a deliberate TTL-stale window, or a bug
   you then fixed.

## Required evidence

- No-cache baseline harness output with p95
- Hit and miss counter output (log, metrics scrape, or admin endpoint)
- After-cache harness output, same command, with computed p95 delta
- Invalidation/TTL rule plus the observed correctness case
- Reflection notes

## Acceptance criteria

- [ ] Baseline p95 without the cache is a number taken from a committed
      harness run.
- [ ] Hit rate is reported as hits / (hits + misses) from counters you
      increment in the running system, not a guessed percentage.
- [ ] After-cache p95 for the identical workload command is reported, and the
      delta vs baseline is a computed number (milliseconds or percent).
- [ ] The invalidation or TTL rule names what write or expiry clears which
      key, and the correctness case records an observed outcome of that rule.

A cache with 0% hits is not automatically a fail if you explain why the
workload never repeated a key — but then the cache must not be claimed as a
latency win.

## Reflection

Answer these in your own words after doing the work:

1. At what hit rate would you keep this cache in production, and which
   measured p95 delta is the reason?
2. What write would make this cache wrong, and how long would a reader see
   the stale value under your rule?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask what the hit counters would show if the key space were unique per
  request (no reuse). If the apprentice cannot answer, they did not think
  about workload shape.
- Do not approve a cache with no invalidation rule.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may explain cache patterns and quiz you on invalidation. It must not
fabricate hit counts or p95 deltas. Disclose material AI assistance with
provider/model, purpose, and verification performed.

## Completion gate

Complete only after the baseline, the counted hit rate, the p95 delta, and the
observed correctness case are submitted and the mentor approves.
