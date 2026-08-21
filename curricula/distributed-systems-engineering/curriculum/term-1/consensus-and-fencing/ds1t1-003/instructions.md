# Quorum Writes and Epoch Fencing Against Split-Brain

**Task ID:** `ds1t1-003`
**Estimated effort:** 18 hours
**Module:** Consensus and Fencing

## Objective

Take the store from `ds1t1-001` / `ds1t1-002` and change the write path so
acknowledgment means a majority has applied the write. Then add an epoch or
fencing token so a partitioned former leader cannot silently overwrite a
newer majority write. You must first reproduce the overwrite with fencing
off, then show the same sequence fail closed with fencing on.

## Why this task exists

The reference SWE path asks you to implement enough Raft to talk about two
leaders and to explain why that may or may not violate safety. This task
goes further: you produce the safety violation as a captured run, then
install the smallest mechanism that makes that exact run refuse the stale
write. "Consensus" here is not a complete protocol — it is a checkable
promise about which writes survive a partition.

LEARN BY DOING. GROW THROUGH MENTORSHIP.

## Authoritative resources

- **MIT 6.5840 - Distributed Systems** (primary): https://pdos.csail.mit.edu/6.5840/

Use the lectures and labs on replication, voting, and terms/epochs. You may
use additional sources; record them in your notes and prefer primary
material over tutorial aggregation sites.

## Setup notes

- Build on the multi-process store. Do not collapse nodes back into one
  process. The harness from `ds1t1-002` is the right place to inject the
  partition that isolates the old leader.
- You do **not** implement a production Raft or Paxos. A majority-ack write
  path plus a monotonically increasing epoch (or fencing token) issued when
  leadership changes is enough. A complete election protocol is allowed
  only if you still produce the two required reproductions.
- Do not claim the result is production-ready consensus.

## Work to complete

1. Change the write path so a `PUT` is acknowledged only after a majority
   of the configured replica set (`N`) has applied it. State `N`, `W`, and
   `R` as integers in the README and keep `W + R > N`. A quorum read must
   contact enough replicas that it cannot miss a committed write.
2. Implement a leadership change that increments an epoch (term, generation,
   or fencing token). Persist the epoch with the log. Every write carries
   the writer's epoch; a replica rejects a write whose epoch is older than
   the highest epoch it has seen.
3. Build an **unfenced** path (or a feature flag that ignores epoch checks)
   and a reproduction script that:
   - commits value `A` under the current leader
   - partitions that leader away from the majority
   - has the remaining majority accept a new leader and commit value `B`
   - heals just enough for the old leader to send value `C` (or a stale `A`)
     without an epoch check
   - shows a later read returning the stale value
   Inject the partition yourself so this is deterministic.
4. Turn fencing on and rerun the identical sequence. The stale write must
   be refused or ignored. A subsequent quorum read must return `B`.
5. Write a `README.md` that names `N`, `W`, `R`, the epoch field, who
   increments it, and which of the two writes is discarded. Include a
   one-paragraph argument for why the fenced system still does **not**
   implement full consensus (what it still cannot do — membership change,
   log conflict resolution across competing majorities, etc.).

## Evidence you'll submit

- Git history with the unfenced quorum store committed **before** the
  fencing change.
- The reproduction script and a captured run of both paths (overwrite, then
  refuse).
- `README.md` with the quorum integers, the epoch field, and the
  not-full-consensus paragraph.
- Reflection notes (see below).

## Acceptance criteria

- [ ] A write is acknowledged only after a majority of the configured
      replica set has applied it; a minority-only apply is not treated as
      committed.
- [ ] The unfenced reproduction deterministically overwrites a newer
      majority write with a stale write from a partitioned former leader,
      and the captured run shows both values.
- [ ] With fencing enabled, the identical sequence refuses or ignores the
      stale leader's write; the majority value is the one a subsequent
      quorum read returns.
- [ ] README names `N`, `W`, and `R` as integers, states `W + R > N`, and
      names the epoch/token field checked on every write — not a general
      claim that "we use consensus."

Check these four yourself before you submit. A mentor will check the same
four things and nothing more subjective than that.

## Reflection

Answer in your own words after doing the work:

1. Why is majority-ack alone not enough to stop the overwrite you
   reproduced? What extra fact does the epoch encode that a vote count
   does not?
2. If two majorities of different memberships both accepted writes (a
   reconfiguration bug), would your fencing still save you? What would
   you need that you did not build?

Also record: what took longer than expected, and what remains unclear
about the gap between "we elect a leader" and "no committed write is
lost."

## Mentor review guide

If a mentor reviews this work, have the apprentice replay the unfenced
script live, then flip the fence and rerun without editing the script's
partition steps. Ask which replica first rejected the stale write, and
why a follower with a higher epoch but a shorter log is still allowed
to refuse. Do not approve a submission that only describes Raft verbally
or that never shows the overwrite.

Suggested review outcome: **Approve**, **Request revision**, or **Create
follow-up challenge**. Prefer questions that force reasoning over
requests for cosmetic polish.

## AI use policy

Mode: **guided**. Explain, hint, and quiz are available; solution
generation is not — generating the fencing logic would skip the exact
mistake this task is designed to make visible. Disclose any material AI
use with provider/model, purpose, and how you verified the result.

## Completion gate

This task is complete only after the evidence is submitted and, when a
mentor is present, the mentor approves the demonstrated competency.
Reading about terms and votes is preparation, not completion.
