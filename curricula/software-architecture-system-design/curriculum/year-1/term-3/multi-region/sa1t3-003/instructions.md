# Multi-Region Topology, Consistency, and Data Residency

**Task ID:** `sa1t3-003`
**Estimated effort:** 9 hours
**Module:** Multi-Region

## Why this task exists

A second region is the most expensive reliability story an architect can
tell, and the easiest to fake on a whiteboard. This task forces three numbers
and one legal boundary onto that whiteboard: how much data you are willing to
lose (RPO), how long you are willing to be down or degraded (RTO), what a
user reads or cannot write after a region dies, and which data class is not
allowed to follow the replica. Those are the decisions. The product names of
the databases are not.

This is not an implementation of replication. It is a topology you can defend
when a reviewer changes the residency rule or the RPO.

## Authoritative resources

- **PostgreSQL Documentation** (primary): https://www.postgresql.org/docs/current/
  — use the high-availability and replication chapters to be precise about
  what synchronous versus asynchronous replication actually guarantees for
  RPO, even if your topology would not use PostgreSQL in every region.

Use official documentation as the primary source. If you use other material,
record it in your notes.

## Work to complete

1. Take the system and NFR budgets from earlier tasks, plus one residency
   constraint you must assume if the brief does not state one (for example:
   "payment-method records of EU customers must be processed and stored in
   the EU"). Write the constraint down before you draw.
2. Choose a topology: primary-failover or active-active. Draw the regions,
   the replication or routing path, and the RPO and RTO as numbers with
   units on the failover path. If you choose active-active, state how write
   conflicts are resolved or avoided.
3. Write an ADR. State the consistency model a user sees after a region
   loss — a stale-read bound, a refused write, a queue that drains later.
   Reject the other topology with a reason tied to an NFR, a cost ceiling,
   or the residency constraint — not "it was more complex."
4. Mark at least one data class as residency-constrained. Name the region or
   jurisdiction and the architectural rule that keeps it there (this class is
   not in the cross-region replica set; this class is tokenized and only the
   token leaves; this class is processed by a region-local service only).

## Required evidence

- A region topology diagram stating active-active or primary-failover, with
  RPO and RTO numbers on the failover path
- An ADR naming the consistency model a user sees after a region loss, and at
  least one rejected topology with a distinct reason
- A note marking at least one data class as residency-constrained, naming the
  region or jurisdiction it must remain in and the architectural rule that
  keeps it there

Submit a repository URL plus a commit reference.

## Acceptance criteria

- [ ] The topology is labelled active-active or primary-failover and states
      RPO and RTO as numbers with units.
- [ ] The ADR states the consistency model users see after a region loss and
      names a rejected topology with a reason other than "it was more
      complex."
- [ ] At least one data class is marked residency-constrained with a named
      region or jurisdiction and a rule that prevents that class from being
      replicated or processed outside it.

## Reflection

1. Which number — RPO, RTO, or the residency rule — actually forbade the
   topology you wanted to draw first?
2. If the residency constraint were removed tomorrow, would you flip the
   topology, or was something else load-bearing?

Also record: what took longer than expected, what you'd practice again, what
remains unclear.

## Mentor review guide

- Change the RPO from minutes to zero (or the reverse) and ask which
  replication mode the ADR now requires. A topology that does not mention
  sync versus async will not survive this question.
- Ask what happens to the residency-constrained class during a failover
  drill. Approve only if the rule still keeps that class inside the named
  jurisdiction.

Suggested outcome: **Approve**, **Request revision**, or **Discuss live**.

## AI use policy

Mode: **guided**. AI may explain replication and RPO/RTO terminology and quiz
your understanding. AI must not choose the topology or write the ADR for your
specific constraint set. Disclose any material AI use.

## Completion gate

This task is not complete when two regions appear on a diagram. It is
complete once you can state RPO, RTO, the user-visible consistency after
loss, and the class that must not leave its region — without looking at the
ADR.
