# Write the Delegation Map Your Calendar Is Hiding

**Task ID:** `el1t1-001`
**Estimated effort:** 8 hours
**Module:** Delegation

## Why this task exists

Most new leads do not fail because they cannot write code. They fail because every interesting problem still routes through them. The calendar looks full; the team looks idle or blocked. "I delegated it" is not evidence a mentor can open. An ownership map and a written brief are.

This is an apprenticeship task, not a reading checkbox. Reading about staff-plus archetypes is preparation. Completion requires artifacts a named owner could execute without a hallway conversation.

## Authoritative resources

- **Staff Engineer (Will Larson)** (primary): https://staffeng.com/ — read the staff-plus archetypes and the material on being a force multiplier, not a hero. You may use additional sources; record them in your notes and prefer primary essays over management-listicle sites.

## Scenario

You are the tech lead of Harborline's **Checkout** team (B2B payments). Mentorship is optional — you do not need a real mentee. Use the roster and the week below as given. If you substitute a real team you lead, keep the same artifact shape and state that you substituted.

**Roster**

| Person | Role | Notes |
| --- | --- | --- |
| You | Tech lead | Still merging most design docs; still jumping on every Sev-2 |
| Morgan | Engineering manager (skip-level for ICs) | Wants predictability, not heroics |
| Jordan | Senior IC | Strong at code; rarely writes the decision down |
| Priya | Mid (3 years) | Reliable; under-delegated; ready for a stretch |
| Sam | Junior (8 months) | Eager; over-scopes; needs tighter briefs |
| Alex | Identity tech lead (other team) | Owns auth; you cannot assign work to Alex |

**Your week (treat every line as a real work item)**

1. Draft the Q3 checkout latency ADR (you started it; it is still in your drafts).
2. Pair with Sam on the refund-retry bug (you have paired three times; Sam has not landed a solo fix).
3. Review Priya's webhook PR (in review for four days; you have not looked).
4. Write the weekly status to Morgan (you wrote the last six yourself).
5. Debug the staging Redis flake (you SSH'd in last time; no note exists).
6. Attend the Identity API office hours (Alex's meeting; you go "just in case").
7. Design the new payouts worker config/secrets approach (you have opinions; no one else has a brief).
8. Interview a staff-engineer candidate (recruiter asked you; Jordan could do it).
9. Update the on-call runbook after last week's Sev-2 (you promised; it is still a sticky note).
10. Answer #checkout-help questions that Jordan or Priya could answer from a FAQ.
11. Prepare the cross-team "rate-limit headers" ask for Identity (no brief exists).
12. Sit in on Sam's design huddle "to make sure it is right."
13. Rewrite Priya's draft RFC because "it will be faster if I just do it."
14. Plan the team's 90-day technical bets (Morgan asked; you have a slide with adjectives).

## Work to complete

1. Classify every item: **keep**, **delegate**, **drop**, or **escalate**. Write a one-line reason that names a risk of the current state (for example, "only you can recover staging Redis").
2. Produce the ownership map as a Markdown table. At least three items must be **delegate**. At least one must be **drop** — a lead who delegates everything and drops nothing is still over-committed.
3. Write **two** delegation briefs for two different owners on the roster (not Alex; you cannot assign across teams here). Each brief must include:
   - a single owner
   - a calendar due date
   - an inspectable done-artifact (a file, a merged PR, a committed runbook section — not "has a handle on it")
   - at least one decision the owner may make without asking you
   - at least one explicit non-goal
   - what you will still do (review, unblock, or nothing)
4. Commit the first drafts.
5. Apply the midpoint constraint: **Priya is already on-call this week and cannot take a second high-interrupt item.** Revise whichever brief or map row that constraint breaks. Commit the revision separately and quote the constraint in the commit message or a `revision-note.md`.

## Required evidence

- An ownership map covering at least ten distinct work items from the Harborline week, each row naming current owner, proposed owner or drop, and a keep/delegate/drop/escalate label with a one-line reason
- Two delegation briefs, each naming a single owner, a due date, an inspectable done-artifact, at least one decision the owner may make without asking, and at least one explicit non-goal
- Git history showing at least one brief revised after the stated midpoint constraint, with the constraint quoted in the commit message or a revision note

Submit a repository URL plus a commit reference. Do not submit a single final document with no history.

## Acceptance criteria

- [ ] The ownership map has at least ten distinct work items; at least three are labeled delegate and at least one is labeled drop.
- [ ] Each of the two briefs names a single owner, a calendar date, an inspectable done-artifact, at least one solo decision, and at least one non-goal.
- [ ] History shows one brief changed after the midpoint constraint ("Priya is already on-call this week"), and the revision note or commit message quotes that constraint.

## Reflection

Answer in your own words after doing the work:

1. Which item was hardest to mark **drop**, and what risk does dropping it actually create?
2. If Priya asked "what may I decide without you?" on each brief, would the written decision boundary be enough, or would they still have to ping you?

Also record: what took longer than expected, what you would practice again, what remains unclear, and which artifact best proves you can delegate in writing.

## Mentor review guide

- Pick one **keep** row and ask why it cannot be delegated to Jordan. Listen for a real constraint versus habit.
- Do not approve briefs whose done-artifact is a feeling ("is comfortable with Redis") or whose solo decision is "ask me if unsure."

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force a keep/drop defense over requests for cosmetic polish.

## AI use policy

Mode: **guided**. AI may explain what makes a brief executable, offer hints if a row is hard to classify, and quiz you on staff-plus archetypes. AI must not generate the map, the two briefs, or the midpoint revision for you — that judgment is the task. Disclose any material AI use with provider/model (if known), purpose, and how you verified the result.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and — if a mentor is present — the mentor approves the demonstrated competency. If you are working without a mentor, complete a second-pass self-review after a day away and record one change you made because of it.
