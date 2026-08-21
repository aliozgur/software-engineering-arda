# Wall-Clock Last-Write-Wins versus Happens-Before

**Task ID:** `ds1t1-004`
**Estimated effort:** 16 hours
**Module:** Clocks and Ordering

## Objective

Give the replicated store two merge policies for concurrent updates to the
same key: last-write-wins (LWW) by wall-clock timestamp, and a version
vector (or pair of vector clocks) that can say "these two writes are
concurrent." A script must lose a write under LWW because of injected clock
skew, then keep both writes (or an explicit conflict) under the vector
policy.

## Why this task exists

`ds1t1-001` showed a stale read. `ds1t1-003` showed a fenced leader. Neither
one forces you to decide what "later" means when two replicas accept writes
without seeing each other. Wall-clock LWW is the default most production
systems quietly ship. This task makes the cost of that default a captured
run, then gives you a merge rule that refuses to pretend the writes were
ordered.

## Authoritative resources

- **MIT 6.5840 - Distributed Systems** (primary): https://pdos.csail.mit.edu/6.5840/

Use the material on time, logical clocks, and consistency models. Record
any extra sources in your notes.

## Setup notes

- Build on the existing multi-process store. You may temporarily allow
  writes at more than one replica (a multi-leader or "any replica accepts
  PUT" mode) so concurrency is real, not simulated inside one process.
- Inject clock skew yourself: a fake clock, an NTP-offset flag, or a
  timestamp the client supplies. Do not wait for real NTP drift.
- Vector clocks and version vectors are both acceptable. Lamport clocks
  alone are **not** enough, because they impose a total order and hide
  concurrency.

## Work to complete

1. Add a `lww` merge policy: each write stores a wall-clock (or injected)
   timestamp; on conflict the higher timestamp wins and the other value is
   discarded.
2. Build a reproduction that:
   - partitions two writable replicas
   - writes `X=1` on replica A with timestamp T1
   - writes `X=2` on replica B with timestamp T2 > T1 even though the B
     write is issued first in real script order (skew)
   - heals and merges
   - shows the surviving value is `1` and `2` is gone
3. Add a `vv` (version-vector) merge policy. Each replica keeps a counter;
   a write from replica R increments R's component. Merge compares vectors:
   - A < B if A is strictly dominated
   - concurrent if neither dominates
   On concurrent writes, keep both values or write a conflict record the
   client can read. Do not silently pick a winner by timestamp.
4. Rerun the identical two writes under `vv`. The captured run must report
   the pair as concurrent and leave both values (or the conflict record)
   inspectable.
5. Write a `README.md` that defines happens-before for this store in terms
   of replica ids and counters, labels the two writes concurrent, and
   states one production situation where you would still choose LWW and
   accept the loss.

## Evidence you'll submit

- Git history with LWW committed before version vectors.
- The reproduction script and captured runs for both policies.
- `README.md` with the happens-before definition and the LWW-acceptable
  situation.
- Reflection notes.

## Acceptance criteria

- [ ] The LWW reproduction injects a clock skew (or an assigned timestamp)
      so the physically earlier write carries the later timestamp, and the
      captured run shows that write winning and the other value gone.
- [ ] The vector-clock (or version-vector) reproduction uses the same two
      writes and reports them as concurrent; both values or an explicit
      conflict record remain inspectable after merge.
- [ ] README states a happens-before rule in terms of replica ids and
      counters (or equivalent), and names the two writes as concurrent
      under that rule.
- [ ] Wall-clock timestamps are not used as the sole merge key in the
      vector policy.

## Reflection

Answer in your own words after doing the work:

1. Why can a Lamport timestamp tell you a total order and still fail to
   tell you the two writes were concurrent?
2. If a client retries the same logical update on two replicas, how would
   you tell "duplicate of one write" from "two concurrent writes"? Did
   your vectors distinguish them?

Also record: what took longer than expected, and what remains unclear
about the difference between "we have a timestamp" and "we have a causal
history."

## Mentor review guide

If a mentor reviews this work, ask the apprentice to add a third replica
and a third concurrent write without changing the merge API, and to say
whether LWW or `vv` still has a defined result. Do not approve a submission
that only defines the clocks in prose or that uses wall-clock time as the
`vv` tie-break.

Suggested review outcome: **Approve**, **Request revision**, or **Create
follow-up challenge**.

## AI use policy

Mode: **guided**. Explain, hint, and quiz are available; solution
generation is not. Disclose any material AI use with provider/model,
purpose, and verification performed.

## Completion gate

This task is complete only after the evidence is submitted and, when a
mentor is present, the mentor approves the demonstrated competency.
