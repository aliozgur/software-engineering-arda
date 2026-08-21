# Ask Another Team for a Change You Cannot Order

**Task ID:** `el1t2-002`
**Estimated effort:** 8 hours
**Module:** Influence

## Why this task exists

You cannot assign work to **Alex** (Identity). You still need a change. Influence without authority is the staff-plus job; it is also the easiest place to submit a story ("I talked to them") instead of an artifact. This task requires a one-page brief, an objection log, and a revised ask that actually changed.

This is an apprenticeship task. Reading about staff-plus influence is preparation. Completion requires the three files.

## Authoritative resources

- **Staff Engineer (Will Larson)** (primary): https://staffeng.com/ — read the material on influence, the tech-lead and staff archetypes, and operating without being the manager. Record extra sources in your notes.

## Scenario

Harborline Checkout is getting webhook storms from retries that Identity cannot distinguish from abuse. You want Identity to add a **`X-Harborline-Attempt`** request header (or equivalent attempt count) on callbacks they send you, so Checkout can apply a documented retry budget instead of treating every call as new.

Alex owns that API. Alex's last written position: "We do not add headers for one consumer. Our mobile clients would have to change. We are in a hiring freeze."

You have no authority. Morgan will not "just tell Identity to do it."

## Work to complete

1. Write a **one-page** brief (aim ≤400 words) that includes:
   - the ask in **one sentence**
   - why it matters to **Identity**, not only to Checkout (their incident load, their abuse-false-positives, their support tickets — pick a real mechanism and state it)
   - **one** thing Checkout will do or fund (implement a client library, write the contract test, take the first on-call week after the change, staff a spike — something costly to you)
2. Write an **objection log** with at least **three** distinct objections in Alex's voice. For each: your response, and whether you concede. At least one concession must be a **scope cut**, a **date move**, or a **funded offer** — not "we will communicate better."
3. Role-play the meeting in writing (both voices) or with a peer playing Alex. Alex must reject the first full ask.
4. Write a **revised ask** that differs from the first in a named scope, date, or offer. Commit it as a separate file. A sentence that only restates the original ask with softer adjectives does not count.

## Required evidence

- A one-page brief that states the ask in one sentence, names a benefit for the other team, and names one thing you will do or fund
- An objection log with at least three distinct objections written in the other lead's voice, each with your response
- A revised ask that differs from the first in a named scope, date, or offer, after the role-play

Submit a repository URL plus a commit reference. History should show brief → log → revised ask, not one file written last.

## Acceptance criteria

- [ ] The brief states the ask in a single sentence, names a benefit for Identity (not only Checkout), and names one thing Checkout will do or fund.
- [ ] The objection log has at least three distinct objections; at least one concession is a scope cut, a date move, or a funded offer — not only "we will communicate better."
- [ ] The revised ask file differs from the first ask in a named scope, date, or offer.

## Reflection

Answer in your own words after doing the work:

1. What did you offer that actually costs Checkout capacity, and what would a cheap offer have been?
2. If Alex still says no after the revision, what is your next written move (not "escalate to Morgan" unless you attach a document)?

Also record: what took longer than expected, what you would practice again, what remains unclear, and which artifact best proves you influenced without authority.

## Mentor review guide

- Ask which concession would still leave Checkout able to enforce a retry budget. If the revision gives away the attempt count entirely, it may be collapse, not influence.
- Do not approve a brief whose "benefit for Identity" is "you will help us."

Suggested review outcome: **Approve**, **Request revision**, or **Discuss live**.

## AI use policy

Mode: **guided**. AI may explain staff-plus influence patterns, offer hints if all objections sound the same, and quiz you on what a costly offer looks like. AI must not write the brief, the objection log, or the revised ask for you. Disclose any material AI use with provider/model (if known), purpose, and verification.

## Completion gate

This task is not complete when you "would have a good meeting." It is complete when the first ask and the revised ask are different in a named way a mentor can diff.
