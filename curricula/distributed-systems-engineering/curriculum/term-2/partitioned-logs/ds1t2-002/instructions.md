# Kafka ISR, acks=all, and Unclean Leader Election

**Task ID:** `ds1t2-002`
**Estimated effort:** 18 hours
**Module:** Partitioned Logs

## Objective

Run Apache Kafka (or a Kafka-protocol cluster you operate yourself) with
three brokers. Produce to a topic with `replication.factor=3`,
`min.insync.replicas=2`, and `acks=all`. Kill brokers until the ISR
shrinks. Reproduce two endings of that sequence: produces fail and acked
offsets survive when unclean leader election is off; at least one acked
offset disappears when it is on.

## Why this task exists

The SWE event-streaming task compares Kafka to a queue and asks you to
keep ordering claims inside a partition. That is vocabulary. This task is
the durability trade-off those docs mention and almost nobody reproduces:
availability versus not electing a leader that never saw the last commit.

## Authoritative resources

- **Apache Kafka Documentation** (primary): https://kafka.apache.org/documentation/
  — replication, ISR, `acks`, `min.insync.replicas`,
  `unclean.leader.election.enable`, consumer groups, and offsets.
- **Docker Get Started** (reference): https://docs.docker.com/get-started/
  — Compose for a three-broker cluster.

Use the official docs for broker configs. Record extra sources.

## Setup notes

- Three brokers, not one broker with `replication.factor=1`. KRaft or
  ZooKeeper mode are both acceptable if you can stop individual brokers.
- A hosted Kafka you cannot kill is not acceptable. Local Compose (or
  equivalent) is.
- You may use a recent Apache Kafka image or a Kafka-compatible broker
  that exposes ISR and unclean-election settings. If the compatible
  broker cannot disable unclean election, use Apache Kafka.
- Inject failures by stopping containers, not by hoping for a crash.

## Work to complete

1. Bring up three brokers and create a topic with `replication.factor=3`,
   at least two partitions, and `min.insync.replicas=2`. Print the
   starting ISR for each partition.
2. Write a producer that uses `acks=all` and records every acked offset
   (partition + offset + payload) to a local file. Write a consumer that
   dumps what it reads to a second file. Commit the cluster and these
   clients before you start killing brokers.
3. **Clean path (`unclean.leader.election.enable=false`):** produce a
   known set of messages. Stop brokers until fewer than two members remain
   in some partition's ISR. Show that further produces fail or do not
   return success. Restart brokers. Consume. Diff the consumer file
   against the acked-offset file — every acked offset must be present.
4. **Unclean path (`unclean.leader.election.enable=true`):** repeat with
   a fresh topic or a reset cluster. Produce, shrink ISR, and force a
   leader that was not in-sync (stop the last in-sync broker while an
   out-of-sync replica remains). Consume after the new leader is elected.
   Name at least one offset that was in the acked file and is missing
   from the consume dump. Print ISR / broker logs around the election.
5. Produce keyed messages and, on a live partition, show that two
   consumers in one group split partitions and that ordering is preserved
   only within a partition — as supporting evidence, not as the main
   claim. README must scope every ordering sentence to a partition.
6. Write a `README.md` that tables the two runs: settings, what the
   producer saw, what the consumer saw, and which acked offset was lost
   (or a statement that none were lost, which is only allowed for the
   unclean=false run). Do not write "exactly-once."

## Evidence you'll submit

- Compose and git history of the cluster before experiments.
- Captured unclean=false run (produce failures + intact acked offsets).
- Captured unclean=true run (named missing acked offset + ISR/logs).
- `README.md` table.
- Reflection notes.

## Acceptance criteria

- [ ] The cluster has three brokers; the experiment topic has
      `replication.factor=3` and `min.insync.replicas=2`; the producer
      uses `acks=all`.
- [ ] The unclean=false run shows produce errors or a bounded wait once
      fewer than two in-sync replicas remain, and a later consume of the
      recovered partition contains every offset the producer marked
      acked.
- [ ] The unclean=true run shows at least one offset the producer treated
      as acked that a consume after failover never returns; the log names
      that offset.
- [ ] README scopes every ordering claim to a single partition and never
      calls the configuration "exactly-once" or "no data loss" without
      naming the unclean-election case that contradicts it.

## Reflection

Answer in your own words after doing the work:

1. What does `acks=all` wait for, exactly — all replicas, or the current
   ISR? Why did that distinction matter in the unclean run?
2. If you needed "never lose an acked produce" and "always accept
   produces while one broker is down," which of those two requirements
   did this cluster force you to drop? Quote the setting.

Also record: what took longer than expected, and what remains unclear
about the difference between "the producer got success" and "the log
still has that offset."

## Mentor review guide

If a mentor reviews this work, ask the apprentice to point at the missing
offset in both files and at the broker log line that elected the unclean
leader. Do not approve a write-up that only restates the Kafka docs.

Suggested review outcome: **Approve**, **Request revision**, or **Create
follow-up challenge**.

## AI use policy

Mode: **guided**. Explain, hint, and quiz are available; solution
generation is not. Disclose any material AI use with provider/model,
purpose, and how you verified each setting against the running brokers.

## Completion gate

This task is complete only after the evidence is submitted and, when a
mentor is present, the mentor approves the demonstrated competency.
A working hello-world producer is not enough.
