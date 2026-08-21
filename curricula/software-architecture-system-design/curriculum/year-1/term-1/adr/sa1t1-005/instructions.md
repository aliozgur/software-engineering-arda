# Defending an Architecture Decision Under a Changed Constraint

**Task ID:** `sa1t1-005`
**Estimated effort:** 6 hours
**Module:** ADR

## Why this task exists

Every decision in this term so far has been written down and reviewed once. This task adds the piece that makes a
decision durable: defending it out loud, in real time, and revising it when a constraint actually changes — rather
than defending it once and treating it as settled forever. This is the closing task of the term and asks for more
independence than the ones before it: you set up the session, not the mentor.

## Authoritative resources

- **adr.github.io** (supporting): https://adr.github.io/ — specifically the guidance on superseding and amending a
  prior ADR rather than deleting it.

## Work to complete

1. Pick one ADR you wrote earlier this term (`sa1t1-002`, `sa1t1-003`, or `sa1t1-004`).
2. Arrange a defense session with your mentor (or, if unavailable, a peer briefed to play a skeptical reviewer).
   Ask them to introduce exactly one changed constraint partway through — a budget cut, a new compliance
   requirement, a revised growth number, a team reorganization — that plausibly affects your decision.
3. Respond live. Take notes on the specific question that most challenged your original reasoning, and on any
   question you could not fully answer.
4. Afterward, write a second ADR that explicitly supersedes or amends the first, addressing the changed constraint.
   Do not rewrite the original from scratch — show what specifically changed and why.

## Required evidence

- The original ADR plus a superseding or amended ADR responding to the mentor's changed constraint
- Notes from the defense session naming the specific question that most challenged the original decision
- A diff or side-by-side note showing exactly what changed between the two ADRs and why

## Acceptance criteria

- [ ] A second ADR marks the first as superseded or amended, rather than replacing it silently.
- [ ] The revision addresses the specific changed constraint raised in the defense, not a generic rewrite.
- [ ] The notes name at least one question the apprentice could not fully answer during the defense.

## Reflection

1. What was the actual weak point the changed constraint exposed — was it a wrong assumption, a missing
   alternative, or a number that was never really load-bearing?
2. What would you set up differently in how you originally wrote the ADR, knowing what the defense revealed?

Also record: what took longer than expected, what you'd practice again, what remains unclear.

## Mentor review guide

- Choose the changed constraint deliberately — it should invalidate a specific part of the original reasoning, not
  the whole decision. The point is a targeted revision, not a teardown.
- Approve based on whether the revision responds to the actual constraint raised, not on how polished the second
  ADR looks.

Suggested outcome: **Approve**, **Request revision**, or **Discuss live**.

## AI use policy

Mode: **guided**. AI may explain, quiz, and — specifically for this task — act as a coach to help you rehearse
defending the original decision before the real session. AI must not draft the revised ADR itself; the revision has
to reflect what you actually learned in the defense. Disclose any material AI use, including any rehearsal session.

## Completion gate

This task is not complete when the second ADR exists. It is complete once the notes show a real question you
struggled with, and the revision responds to that specific gap rather than smoothing it over.
