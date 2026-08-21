# Design a Stretch Assignment You Will Not Rescue

**Task ID:** `el1t1-004`
**Estimated effort:** 8 hours
**Module:** Stretch

## Why this task exists

Term 1 opened with a delegation map. This task is the harder version: a **stretch** — work the owner has not done before — with a plan for what you will inspect and what you will refuse to take back. Without kill-criteria, stretch work becomes a Sunday rescue and a story about how "they weren't ready."

This is an apprenticeship task. Reading is preparation. Completion requires a brief, a check-in plan, and a midpoint note — not a claim that you "gave someone a chance."

## Authoritative resources

- **Staff Engineer (Will Larson)** (primary): https://staffeng.com/ — read the material on sponsorship versus dumping, and on multiplying other engineers.
- **The Twelve-Factor App** (reference): https://12factor.net/ — especially **III. Config**. The stretch is about Harborline config and secrets, not about rewriting the Twelve-Factor site.

## Scenario

**Priya** (mid, 3 years) will own this stretch. You remain Harborline Checkout tech lead. Mentorship is optional; you do not need Priya to be a real person.

**Assignment (do not replace the outcome):** Priya will propose how the new **payouts worker** gets its config and secrets — following Twelve-Factor **III. Config** (config in the environment, secrets not baked into the image). The inspectable done-artifact is a short RFC plus a worked example (env var list **or** a stub `README` that shows how a new engineer would run the worker locally without a copied `.env` from production).

**Constraints you must include (you may add more, you may not drop these):**

- Production secrets must not appear in the repository or in a committed `.env.example` with real values.
- Identity's vault is not available to Checkout for another six weeks (Alex said so in writing).
- The worker must be runnable by a new engineer in under 20 minutes from the RFC plus example.

**Midpoint surprise (apply after the first draft of the brief and plan):** Priya messages you: "I started writing the Dockerfile `ENV PAYOUT_SECRET=...` so staging works. Can you just finish the RFC tonight? Morgan is asking."

## Work to complete

1. Write the stretch brief:
   - single owner (Priya)
   - inspectable done-artifact
   - at least two constraints (the three above count)
   - decisions Priya may make without you (for example: which env-var names, whether to use a local dummy secret file that is gitignored)
   - at least **three** items on an **I will not do this for you** list (implement the worker, rewrite the RFC the night before, paste production secrets into their example, and similar)
   - what "killed" looks like: a dated criterion that turns this back into scoped-down work or a different owner
2. Write a check-in plan with **three** calendar dates between assignment and due date. Each date names the **file, PR, or doc** you will open that day. "How are you feeling?" is not an inspection.
3. Commit those two artifacts.
4. Write the midpoint stuck-note as if you already received Priya's message. Record either a **hint** you sent (not the finished RFC) or a **scope cut** you made. Name **one** implementation you refused (the Dockerfile secret, finishing the RFC tonight, or similar). Commit this as a third file.

## Required evidence

- A stretch brief naming one owner, one inspectable done-artifact, at least two constraints, and at least three items on an "I will not do this for you" list
- A check-in plan with three dated inspections, each naming the artifact the lead will open (not a mood check)
- A midpoint stuck-note that records a hint or a scope cut and states what the lead refused to implement

Submit a repository URL plus a commit reference. History should show the midpoint note after the brief, not one combined paste.

## Acceptance criteria

- [ ] The brief names a single owner, one inspectable done-artifact, at least two constraints, and at least three items the lead will not implement for the owner.
- [ ] The check-in plan has three calendar dates; each date names a specific file, PR, or doc the lead will inspect.
- [ ] The midpoint note describes a stuck moment, records either a written hint or a written scope cut, and names one implementation the lead refused to do.

## Reflection

Answer in your own words after doing the work:

1. If Morgan asked tomorrow why the RFC is not done, what sentence in the brief protects Priya from being described as "slow"?
2. Which "I will not" item was hardest to keep, and what would breaking it teach Priya?

Also record: what took longer than expected, what you would practice again, what remains unclear, and which artifact best proves you designed a stretch instead of a rescue.

## Mentor review guide

- Ask what the kill-criteria date is and what happens the morning after it. If the answer is "I would just finish it," request revision.
- Do not approve a check-in plan whose inspections are conversations with no named file.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**.

## AI use policy

Mode: **guided**. AI may explain Twelve-Factor config, offer hints if the kill-criteria are vague, and quiz you on sponsorship versus rescue. AI must not write the brief, the check-in plan, or the midpoint note for you. Disclose any material AI use with provider/model (if known), purpose, and verification.

## Completion gate

This task is not complete when Priya "has a stretch." It is complete when a mentor can see the line you will not cross and the three artifacts you would actually open on the check-in dates.
