# Evolving a Running Architecture Without a Big-Bang Rewrite

**Task ID:** `sa1t3-005`
**Estimated effort:** 8 hours
**Module:** Evolution

## Why this task exists

Term 1 compared styles. Term 3 asks you to leave a style you already chose
without pretending the current system will be turned off on a Friday. The
work is the overlap: two writers, two read paths, or old and new consumers
running at once, and a contract that must hold while they do. An architect
who can only describe the destination has not planned an evolution. An
architect who can name the last reversible step has.

Reading about strangler-fig or expand-contract patterns is preparation.
Completion requires a three-step sequence, a compatibility ADR, and a
rollback trigger that is inspectable.

## Authoritative resources

- **adr.github.io** (primary): https://adr.github.io/ — you will supersede or
  amend a prior style or communication ADR; do not delete it.
- **The Twelve-Factor App** (supporting): https://12factor.net/ — disposability
  and backing services are what make a dual-running step survivable. If a
  factor does not apply to a step, say so.

Use official documentation as the primary source. If you use other material,
record it in your notes.

## Work to complete

1. Pick one prior decision to evolve — the style from `sa1t1-003`, the
   communication style from `sa1t1-004`, or the storage split from
   `sa1t2-001`. State the current state and the destination in one sentence
   each. The destination must be a genuine change, not a rename.
2. Write a sequence of at least three steps. For each step, name what is
   dual-running and which clients or writers have moved. A step that is only
   "then we cut over" is not a step; name the expand, the migrate, and the
   contract (or an equivalent three).
3. Write an ADR for the compatibility contract that must hold for the whole
   overlap — an API field that cannot be removed, an event schema version
   that both consumers accept, a dual-write invariant. Name at least one
   change that is forbidden during the overlap. Mark the prior ADR as still
   in force or superseded.
4. Write a rollback note: the last step that is still reversible, by number,
   and the inspectable evidence that would trigger rollback (an SLI from
   `sa1t2-005`, a contract-test failure, a dual-write mismatch count).

## Required evidence

- A migration sequence of at least three steps that names, for each step,
  what is dual-running and which clients or writers have moved
- An ADR stating the compatibility contract that must hold for the whole
  overlap, and marking the prior target-style ADR as still in force or
  superseded
- A rollback note naming the last step that is still reversible and the
  inspectable evidence that would trigger rollback

Submit a repository URL plus a commit reference.

## Acceptance criteria

- [ ] The sequence has at least three steps, and each step names what is
      dual-running.
- [ ] The ADR states a compatibility contract that must hold for the overlap
      and names at least one change that is forbidden during that overlap.
- [ ] The rollback note names the last reversible step by number and names
      the evidence that would trigger rollback.

## Reflection

1. Which step did you want to skip, and what would have been un-rollbackable
   if you had?
2. What would have to be true for a big-bang cutover to be the more honest
   plan — and is that true of your current system?

Also record: what took longer than expected, what you'd practice again, what
remains unclear.

## Mentor review guide

- Point at step two and ask who is still writing the old path. If the
  apprentice cannot name a client, the dual-running claim is decorative.
- Do not approve a rollback trigger that is "if it looks bad."

Suggested outcome: **Approve**, **Request revision**, or **Discuss live**.

## AI use policy

Mode: **guided**. AI may explain expand-contract and dual-write vocabulary
and quiz your understanding. AI must not write the sequence or the
compatibility contract for your specific prior decision. Disclose any
material AI use.

## Completion gate

This task is not complete when a destination style is named. It is complete
once each step names what is dual-running, and you can state the last
reversible step and the evidence that would send you back.
