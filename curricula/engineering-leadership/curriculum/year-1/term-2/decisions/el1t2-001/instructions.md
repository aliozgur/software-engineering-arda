# Write the ADR Other Teams Have to Live With

**Task ID:** `el1t2-001`
**Estimated effort:** 8 hours
**Module:** Decisions

## Why this task exists

Term 1 was about people on your team. Term 2 starts with a decision **other teams have to live with**. If the ADR only records what Checkout prefers, it is a diary. If it names who pays, what they must change, and what you rejected, it is a leadership artifact a mentor can inspect.

This is an apprenticeship task. Reading Twelve-Factor is preparation. Completion requires a committed ADR, an impact table, and a visible revision after a sister-team constraint.

## Authoritative resources

- **The Twelve-Factor App** (primary): https://12factor.net/ — read **III. Config**, **XI. Logs**, and **IV. Backing services** before you decide. You will cite at least one factor by number or official name. Prefer the primary text over blog summaries.

## Scenario

Harborline's platform group asked Checkout to propose a **company-wide** rule for how services get config and secrets, and how they write logs. You are drafting the ADR. Teams that will be affected if this lands:

| Team | Current state |
| --- | --- |
| Checkout (you) | Some secrets in repo; logs are `print` and files on the box |
| Identity (Alex) | Uses a vault; cannot take a new shared contract for six weeks |
| Mobile (client) | Embeds a staging API key in a flavor config; will need a new build pipeline |
| Data platform | Tails application log files from VMs; a stdout-only rule breaks their job |

**Decision you must make (pick one; do not pick a fourth "do all later"):**

- **A.** All services must take config and secrets from the environment (Twelve-Factor III). Images contain no secrets.
- **B.** All services must treat logs as event streams to stdout (Twelve-Factor XI). No app-owned log files.
- **C.** Backing services (Redis, the Identity API, the warehouse) are attached via config, not hardcoded hosts (Twelve-Factor IV).

**Midpoint constraint (apply after the first committed draft):** Alex writes: **"Identity cannot meet a company-wide cutover in this quarter. If you set a date we cannot meet, we will formally object."**

You must revise date, scope, or phasing — not add a sentence that says "we will communicate." "Do both A and B with no cut" is not a revision.

## Work to complete

1. Write the ADR: context, decision (A, B, or C), at least **two** rejected alternatives (the other letters, or a serious "keep the status quo" / "per-team choice" option), each with a **distinct** reason, and consequences including **at least one negative** consequence of the chosen option.
2. Write an impact table with at least **three** teams. Each row: team, required change, owning team (usually themselves).
3. Cite at least one Twelve-Factor factor by number or official name — as a constraint you are applying, or as a **misapplication you are rejecting** (for example, "stdout logs without a collector would drop Data's tailing job").
4. Commit the first complete draft.
5. Apply Alex's constraint. Change the date, the scope (which teams, which phase), or both. Commit separately. Quote Alex's constraint in the commit message or `revision-note.md`.

## Required evidence

- An ADR in a context/decision/consequences shape that names at least two rejected alternatives with distinct reasons and at least one accepted negative consequence
- An impact table with at least three teams, each row naming a required change and the owning team
- A citation of at least one Twelve-Factor factor by number or official name as a constraint or as a rejected misapplication
- Git history showing a date or scope revision after the Identity constraint, with that constraint quoted in the commit message or revision note

Submit a repository URL plus a commit reference.

## Acceptance criteria

- [ ] The ADR names at least two rejected alternatives, each with a reason distinct from "it was worse," and states at least one negative consequence of the chosen option.
- [ ] The impact table lists at least three teams; each row names a concrete change and an owning team.
- [ ] The ADR cites at least one Twelve-Factor factor by number or official name.
- [ ] History shows the date or scope changed after the stated Identity constraint, and the revision note or commit message quotes that constraint.

## Reflection

Answer in your own words after doing the work:

1. Which team's cost did you almost leave out of the first draft, and what would they have had to discover on their own?
2. What would have to be true for you to reverse this ADR in six months?

Also record: what took longer than expected, what you would practice again, what remains unclear, and which artifact best proves this is an org-scope decision.

## Mentor review guide

- Ask the apprentice to argue for the rejected alternative they find hardest to dismiss, using only what is in the ADR.
- Do not approve an impact table that lists teams but not a change ("Identity: informed").

Suggested review outcome: **Approve**, **Request revision**, or **Discuss live**.

## AI use policy

Mode: **guided**. AI may explain Twelve-Factor factors, offer hints if an alternative is a strawman, and quiz you on what belongs in consequences. AI must not draft the decision, the alternatives, the impact table, or the revision for you. Disclose any material AI use with provider/model (if known), purpose, and verification.

## Completion gate

This task is not complete when the ADR file exists. It is complete when a sister-team lead could object from the written impact, and the history shows you changed date or scope after Alex's constraint — not only added adjectives.
