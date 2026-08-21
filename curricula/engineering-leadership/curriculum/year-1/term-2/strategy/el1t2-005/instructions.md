# A 90-Day Technical Strategy You Can Be Held To

**Task ID:** `el1t2-005`
**Estimated effort:** 10 hours
**Module:** Strategy

## Why this task exists

This is the capstone of the path. You have mapped work, run a 1:1, reviewed without taking the keyboard, designed a stretch, written an org-scope ADR, asked another team for a change, led incident comms, and signed an ethics recommendation. A lead still owes the team a **time-bounded** technical strategy: what we will bet on, what we will stop, who owns each bet, and which bet dies if a constraint changes.

"Be more reliable and mentor more" is not a strategy. Three bets with inspectable 90-day outcomes are.

This is an apprenticeship task. Reading staff-plus strategy material is preparation. Completion requires the memo, the constraint-change note, and the EM one-pager.

## Authoritative resources

- **Staff Engineer (Will Larson)** (primary): https://staffeng.com/ — read the material on setting a technical direction and on saying no.
- **The Twelve-Factor App** (reference): https://12factor.net/ — at least one bet must cite a factor or your `el1t2-001` decision.

If you have not completed `el1t2-001`, cite a factor directly and state that you did not have a prior ADR.

## Scenario

You remain Harborline Checkout tech lead. **Today's constraints** (do not ignore these):

- Team: you, Jordan, Priya, Sam. No new headcount this quarter.
- Morgan wants a written 90-day plan, not a slide of adjectives.
- Last quarter the team started **four** things and finished one.
- Current work that is actually happening (you must stop **one** of these, not a fictional fifth):
  1. A rewrite of the invoice PDF renderer "while we are in there"
  2. Weekly "platform cleanup" with no owner and no done-artifact
  3. You still writing the status report and sitting in Identity office hours
  4. An unofficial second dashboard Sam started after the 1:1

**Constraint change (apply after the first complete memo):** Morgan writes: **"We lose Priya for six weeks (parental leave). Error budget for checkout latency is already spent this month. Cut or descope one bet. Do not add a fourth."**

## Work to complete

1. Write the strategy memo:
   - current constraint in ≤10 lines
   - **exactly three** bets; each bet: one-sentence intent, **90-day inspectable outcome** (a merged RFC, an ADR adopted by two teams, a runbook section, a measured p99 — not "better mentoring"), and a **named owner** from the roster (you may own at most one bet)
   - **exactly one stop**: one of the four current-work items above, with one sentence on what happens to the leftover work
   - at least one bet cites a **Twelve-Factor** factor by number or name, **or** your `el1t2-001` decision (A/B/C or title)
2. Write a **delegation appendix**: for each bet, what you will inspect and what you will not implement (reuse the muscle from Term 1; do not paste Term 1 files wholesale).
3. Commit the memo.
4. Write the **constraint-change note** (≤300 words): which bet is cut or descoped, why that one (not "we will try harder with three people"), and what the 90-day outcome becomes if descoped.
5. Write the **EM one-pager** for Morgan (≤400 words) that still contains the three bets and the stop. No appendix required on this page.
6. Commit the note and the one-pager separately.

## Required evidence

- A strategy memo that names exactly three bets and one stop, each bet with a 90-day inspectable outcome and a named owner from the Harborline roster
- At least one bet that cites a Twelve-Factor factor or a decision from el1t2-001 by name
- A constraint-change note of at most 300 words that cuts or descopes a named bet after the headcount or error-budget constraint
- An EM one-pager of at most 400 words that still contains the three bets and the stop

Submit a repository URL plus a commit reference. Do not submit one final blob with no history.

## Acceptance criteria

- [ ] The memo names exactly three bets and one stop; each bet has a 90-day inspectable outcome and a named owner on the Harborline roster.
- [ ] The stop names work the team is currently doing, not a hypothetical future project.
- [ ] At least one bet cites a Twelve-Factor factor by number or name, or cites the el1t2-001 decision by title or letter.
- [ ] The constraint-change note is at most 300 words and names which bet is cut or descoped and why.
- [ ] The EM one-pager is at most 400 words and includes the three bets and the stop.

## Reflection

Answer in your own words after doing the work:

1. Which bet would you cut if Morgan's note had arrived *before* you wrote the memo, and did you actually cut that one?
2. If a mentor opened only the EM one-pager, what would they be unable to hold you to that the full memo makes checkable?

Also record: what took longer than expected, what you would practice again, what remains unclear, and which artifact best proves you can be held to a 90-day plan.

## Mentor review guide

- Pick one "inspectable outcome" and ask what file or number you would open on day 90. If the answer is a feeling, request revision.
- Do not approve a stop that is "be less heroic" or "stop doing low-value work" without naming one of the four current items.

Suggested review outcome: **Approve**, **Request revision**, or **Discuss live**. Prefer a constraint-change defense over polish.

## AI use policy

Mode: **guided**. AI may explain what makes a bet inspectable, offer hints if all three bets are really one bet restated, and quiz you on staff-plus direction-setting. AI must not generate the three bets, the stop, the constraint-change note, or the EM one-pager for you. Disclose any material AI use with provider/model (if known), purpose, and verification.

## Completion gate

This task is not complete when the memo sounds like leadership. It is complete when a mentor can name the stop, the three day-90 artifacts, and which bet dies when Priya is out — from the files alone.
