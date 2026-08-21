# Hash Partitions, a Hotspot, and a Reshard Window

**Task ID:** `ds1t2-001`
**Estimated effort:** 16 hours
**Module:** Partitioning

## Objective

Split the key space of your store across at least three shard processes.
Drive a workload that overloads one shard and print the counts. Then move
at least one partition to a new owner and capture a window where a named
key is unreadable, double-owned, or both. End with a falsifiable reshard
contract.

## Why this task exists

Term 1 taught you how replicas disagree. Term 2 starts with how keys are
owned. A partition map is a distributed system of its own: during a
reshard, "the key exists" is temporarily a question with two answers. The
SWE path never measures that window. This task does.

## Authoritative resources

- **MIT 6.5840 - Distributed Systems** (primary): https://pdos.csail.mit.edu/6.5840/
  — use the labs and notes on sharding / key-value servers if you have
  them; otherwise apply the same failure-first reasoning you used on
  replicas.
- **Docker Get Started** (reference): https://docs.docker.com/get-started/
  — optional but useful if each shard is a container.

## Setup notes

- Build on the store from Term 1 or a slimmed descendant. Shards must be
  separate OS processes. A hash function inside one process that writes
  into three maps is not partitioning.
- Consistent hashing, modulo hashing, or explicit ranges are all fine.
  State the function in the README.
- You may keep a separate router/proxy process. The router is allowed to
  be a single process; the shards are not.

## Work to complete

1. Implement a static partition map: at least three shards, each owning a
   disjoint portion of the key space. Route `PUT`/`GET` by the map. A
   happy-path `GET` contacts one shard, not all of them.
2. Write a load script with a key distribution you control. First run a
   uniform (or well-spread) baseline and print per-shard counts. Then run
   a hotspot distribution (one key, or a tiny key set that hashes to one
   shard) and show one shard receiving at least 3x the requests of each
   other named shard.
3. Implement a reshard that moves at least one partition (or one hash
   bucket) from shard A to shard B. Do this as an explicit sequence of
   steps you log — for example: freeze writes, copy keys, flip the map,
   unfreeze — not as a silent restart with a new config.
4. During that sequence, issue `GET`/`PUT` against a named migrating key
   on a timer. Capture a window (start and end timestamps or step numbers)
   where the key is unreadable, returned by both owners, or returned with
   two different values. If your protocol is careful enough that none of
   those happen, you must instead show a refused request (`503` or
   equivalent) for every request in the window and still record the
   window bounds.
5. Write a `README.md` that names the hash/range function, the partition
   count, and a falsifiable reshard contract: what a client is guaranteed
   to see during a migration, and what it is not.

## Evidence you'll submit

- Git history in the order: single-shard → static map → reshard.
- Hotspot run with per-shard counts.
- Reshard log with window bounds and the named key's outcomes.
- `README.md` with the contract.
- Reflection notes.

## Acceptance criteria

- [ ] At least three shard processes own disjoint key ranges or hash
      buckets; a GET is routed by the partition map, not by broadcasting
      to every shard on the happy path.
- [ ] The hotspot run prints per-shard request counts and one shard is at
      least 3x any other named shard.
- [ ] The reshard run records a non-empty window (start and end) during
      which a named key is unreadable, served by two owners, or served
      with two different values.
- [ ] README states a falsifiable reshard contract rather than
      "resharding is available."

The refused-request alternative in step 4 satisfies the third criterion
only if the window bounds and the refuse reason are in the log.

## Reflection

Answer in your own words after doing the work:

1. Which was harder to make deterministic: the hotspot or the reshard
   window? What assumption failed?
2. If you added replication inside each shard (Term 1), where does a
   reshard have to wait for a majority, and what does the client see
   while it waits?

Also record: what took longer than expected, and what remains unclear
about owning a key versus storing a key.

## Mentor review guide

If a mentor reviews this work, pick a key the apprentice did not mention
and ask which shard owns it after the reshard, then have them prove it
from the map and a live `GET`. Do not approve a reshard that is only a
config reload with no logged window.

Suggested review outcome: **Approve**, **Request revision**, or **Create
follow-up challenge**.

## AI use policy

Mode: **guided**. Explain, hint, and quiz are available; solution
generation is not. Disclose any material AI use with provider/model,
purpose, and verification performed.

## Completion gate

This task is complete only after the evidence is submitted and, when a
mentor is present, the mentor approves the demonstrated competency.
