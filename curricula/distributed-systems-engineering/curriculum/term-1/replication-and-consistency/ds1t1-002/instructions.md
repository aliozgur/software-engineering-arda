# Partition Behavior and the Availability Contract

**Task ID:** `ds1t1-002`
**Estimated effort:** 14 hours
**Module:** Replication and Consistency

## Objective

Extend the store from `ds1t1-001` with a failure-injection harness that can
kill, pause, or network-partition any single node on demand. For each of the
three failure classes, write down your prediction for what happens to reads
(under both modes) and writes *before* you run anything, then run enough
trials to find out whether you were right, and end with a precise,
falsifiable availability contract.

## Why this task exists

CAP is folklore until you've had to commit to a prediction in writing and
then watched a process you `kill -9`'d prove you wrong. This task is about
that gap — and about learning to write availability guarantees as specific,
checkable rules instead of vibes ("the system stays mostly available").

## Setup notes

- Build on `ds1t1-001` directly; don't start a new store from scratch.
- A "network partition" here means dropping packets between two named
  processes without killing either one — a local firewall rule, an
  iptables/pf rule, or a small TCP proxy you can toggle are all fine.
  A partition is not the same failure as a kill or a pause; treat all three
  as distinct.

## Work to complete

1. Build a harness with three independent failure injectors:
   - **Kill** — `kill -9` (or equivalent) a named node, then restart it and
     let it rejoin/catch up.
   - **Pause** — suspend a named node (e.g. `SIGSTOP`/`SIGCONT`) to simulate
     a hang without a crash, then resume it.
   - **Partition** — drop network traffic between two named processes
     without touching a third, then heal the partition.
2. Before running anything, write down your prediction for each of the three
   failure classes: what happens to writes, and what happens to reads under
   `strict` and under `relaxed` mode. Commit this prediction (timestamped, in
   git) before you run the corresponding trials.
3. Run each failure class at least 5 times and record the actual outcome
   each time — 15+ trials total.
4. Where a prediction and an actual outcome disagree, write down why, in the
   README.
5. State your system's availability contract as a specific rule, for example:
   "a write submitted while the leader cannot reach a majority of followers
   is refused within 2 seconds, and is never silently accepted and later
   dropped." Vague claims like "the system is highly available" don't count.

## Evidence you'll submit

- Harness code and git history showing the three injectors built
  incrementally.
- A results log for all 15+ trials with predicted and actual outcome for
  each.
- README stating the availability contract as a specific, falsifiable rule.
- Reflection notes.

## Acceptance criteria

- [ ] The harness can independently kill, pause, and network-partition a
      single named node without affecting the others — shown by trial logs,
      not asserted from source alone.
- [ ] At least 15 recorded trials exist (3 classes x 5+ trials) with both a
      predicted and an actual outcome per trial.
- [ ] At least one prediction/outcome mismatch is documented with an
      explanation — or, if genuinely none occurred, all 15 predictions carry
      timestamps preceding their corresponding trial runs, so a mentor can
      verify the predictions weren't backfilled.
- [ ] The availability contract is a specific, falsifiable rule, not a
      general claim.

## Reflection

Answer in your own words:

1. Which of the three failure classes most surprised you, and specifically
   what assumption of yours turned out to be wrong?
2. Is your `relaxed` read mode "available" during a partition in a way that
   is actually useful, or just available in the sense that it returns
   *something*? Where's the line?

Also record what took longer than expected and what part of the availability
contract you're least confident would survive a harder adversary.

## AI use policy

Mode: **guided**. Explain, hint, and quiz are available; solution generation
is not. Disclose any material AI use with provider/model, purpose, and
verification performed.
