# PostgreSQL Streaming Replication, Lag, and Dual-Primary Writes

**Task ID:** `ds1t1-005`
**Estimated effort:** 22 hours
**Module:** Database Replication

## Objective

Stand up PostgreSQL streaming replication (one primary, at least one
replica) under Docker. Show a stale read caused by apply lag you injected.
Promote the replica. Then either fence the old primary so it cannot accept
writes, or deliberately leave it writable and capture the divergent row.
You must record timeline or LSN evidence either way.

## Why this task exists

Term 1 so far has been a store you control. Production teams still lose
data on failover because the old primary was not fenced and because
asynchronous apply looks "up" while serving yesterday's row. The SWE
curriculum never runs this. This task is the first time the replica is a
real database, the lag is a real LSN, and the split-brain is a real pair
of timelines.

## Authoritative resources

- **PostgreSQL Documentation** (primary): https://www.postgresql.org/docs/current/
  — start from *High Availability, Load Balancing, and Replication* and the
  sections on streaming replication, `pg_ctl promote`, replication slots,
  and `pg_rewind` / timeline history.
- **Docker Get Started** (reference): https://docs.docker.com/get-started/
  — use Compose (or equivalent) so a clean `up` reproduces the cluster.

Use the official docs as the source of truth for GUCs and promote steps.
Record any extra sources.

## Setup notes

- PostgreSQL 16 or newer is preferred. Do not substitute a mock SQL engine.
- Two containers (or two data directories on two processes) are the
  minimum. A dump taken on a timer is not streaming replication.
- You may use a published Compose recipe as a starting point, but the
  failover, lag injection, and fencing steps must be yours and committed
  incrementally.
- Inject lag by pausing the replica (`docker pause`), delaying WAL apply,
  or using `recovery_min_apply_delay`. Do not rely on incidental slowness.

## Work to complete

1. Write Compose (or equivalent) that starts a primary with a replication
   role and a hot standby streaming from it. Commit this before you add
   failover scripts.
2. Create a small table, insert a row on the primary, confirm it appears
   on the replica. Record `pg_stat_replication` (or `pg_stat_wal_receiver`)
   output in the evidence log.
3. Inject apply lag. Write a new row on the primary. Read the replica and
   show the new row missing (or an older value). Capture the replica's
   replay LSN / `replay_lag` at that moment, and the primary query that
   returns the new row. Heal the lag and show the replica catch up.
4. Promote the replica (`pg_ctl promote` or `pg_promote()`). Write a new
   row on the new primary. Record the timeline ID and a write LSN.
5. Point a client at the **old** primary:
   - Either fence it (stop Postgres, `pg_rewind`, or reject connections
     with `recovery` / a firewall / removing it from the connection
     string **and** shutting down the postmaster) and show a refused
     write,
   - or leave it writable on purpose, write a conflicting value for the
     same key, and capture both nodes' rows plus both timeline IDs.
   README must say which path you took and why.
6. Write a `README.md` that states async vs sync (`synchronous_standby_names`
   empty or not), the lag metric you used, and the fencing method. Include
   a one-paragraph comparison to the store from `ds1t1-003`: what did
   Postgres already give you (WAL, timelines) that your epoch field was
   approximating?

## Evidence you'll submit

- Compose files and git history in the order: primary-only → replica →
  failover/fence.
- Captured lag run with LSN / `replay_lag` numbers.
- Captured failover run with timeline IDs or LSNs, plus either a refused
  old-primary write or divergent rows.
- `README.md` as specified.
- Reflection notes.

## Acceptance criteria

- [ ] Primary and replica run as separate containers (or VMs) using
      PostgreSQL streaming replication, not a single-instance logical copy
      or a dump/restore loop.
- [ ] The lag demonstration records a replica LSN or replay lag number at
      the moment of the stale read, and the same query on the primary
      returns the new row.
- [ ] After promote, the new primary accepts a write that is not on the
      old primary's timeline; the captured log includes timeline IDs or
      LSNs for both sides.
- [ ] README names either a working fence (old primary refuses clients or
      is shut down before clients are pointed at the new primary) or, if
      the dual-primary write was left unfenced on purpose, the conflicting
      row values on both nodes.

## Reflection

Answer in your own words after doing the work:

1. Under asynchronous replication, which of the following did you actually
   lose on promote, if anything: acknowledged writes, unacknowledged
   writes, or neither? Point at the LSN evidence, not a slogan.
2. How is a PostgreSQL timeline different from the epoch you added in
   `ds1t1-003`? What can a timeline ID tell a replica that a counter
   cannot?

Also record: what took longer than expected, and what remains unclear
about when a replica is safe to serve reads.

## Mentor review guide

If a mentor reviews this work, ask the apprentice to explain whether
`synchronous_commit` on the primary would have made the stale read
impossible, and at what availability cost. Have them show the
`pg_stat_replication` row, not a screenshot of a GUI. Do not approve a
failover that never records a timeline or LSN.

Suggested review outcome: **Approve**, **Request revision**, or **Create
follow-up challenge**.

## AI use policy

Mode: **guided**. Explain, hint, and quiz are available; solution
generation is not — especially not a generated failover runbook you did
not execute. Disclose any material AI use with provider/model, purpose,
and how you verified each captured command against a live cluster.

## Completion gate

This task is complete only after the evidence is submitted and, when a
mentor is present, the mentor approves the demonstrated competency.
A Compose file that starts two containers is not enough.
