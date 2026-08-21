# Writing Your First Architecture Decision Record

**Task ID:** `sa1t1-002`
**Estimated effort:** 5 hours
**Module:** ADR

## Why this task exists

Architecture decisions that live only in someone's head, or in a Slack thread, cannot be reviewed, questioned, or
safely revisited when circumstances change. The Architecture Decision Record (ADR) is the unit of accountable
architectural judgment this whole curriculum is built around. Before analyzing bigger trade-offs, you need to be
able to write one that a skeptical reader could actually use.

Reading about the ADR format is preparation. The task is complete only once you have a real, committed ADR that
names what you rejected and why.

## Authoritative resources

- **adr.github.io** (primary): https://adr.github.io/ — read the "why" and look at a couple of example templates
  before you write. You are not required to use any specific template verbatim; the required content is the
  content described below, not a specific heading layout.

## Work to complete

1. Pick a real architectural decision: something from a project you've worked on, from one of your NFR budgets in
   the previous task, or a decision your mentor assigns. It must be a genuine decision with real alternatives, not
   a decision with an obviously correct answer.
2. Write the ADR: state the context and the specific NFR or constraint driving it, the decision made, at least two
   alternatives that were seriously considered and rejected (each with its own distinct reason), and the
   consequences of the chosen option — including at least one negative consequence or accepted trade-off.
3. Commit it.
4. Get one round of review — from a mentor, a peer, or your own second pass after a day away from it — and revise
   the ADR in response to at least one real gap found. Commit the revision separately so the change is visible.

## Required evidence

- The ADR file itself, committed to a repository, in a context/decision/consequences shape
- At least two rejected alternatives named in the ADR, each with a reason distinct from the others
- Git history showing at least one revision of the ADR after a stated review comment or a self-identified gap

## Acceptance criteria

- [ ] The ADR names at least two rejected alternatives, each with a stated reason distinct from "it was worse."
- [ ] At least one negative consequence or accepted trade-off of the chosen option is stated explicitly.
- [ ] The ADR is traceable to at least one NFR budget or explicit constraint it responds to.

## Reflection

1. What made the two rejected alternatives genuinely tempting, rather than obviously wrong?
2. What would have to be true for you to reverse this decision later?

Also record: what took longer than expected, what you'd practice again, what remains unclear.

## Mentor review guide

- Ask the apprentice to argue for the rejected alternative they find hardest to dismiss. A well-written ADR should
  make this possible without inventing new information.
- Do not approve an ADR whose "rejected alternatives" are strawmen no one would seriously propose.

Suggested outcome: **Approve**, **Request revision**, or **Discuss live**.

## AI use policy

Mode: **guided**. AI may explain what makes an ADR complete, quiz you on the format, and offer hints if you're
stuck naming a genuine alternative. AI must not draft the decision, the alternatives, or the consequences for you —
that judgment is the task. Disclose any material AI use.

## Completion gate

This task is not complete when the ADR file exists. It is complete once the ADR has survived one round of real
critique and been revised in response to it.
