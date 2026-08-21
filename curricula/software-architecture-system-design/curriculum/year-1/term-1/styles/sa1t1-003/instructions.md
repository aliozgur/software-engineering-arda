# Monolith vs. Microservices: A Defensible Comparison

**Task ID:** `sa1t1-003`
**Estimated effort:** 7 hours
**Module:** Styles

## Why this task exists

"Monolith vs. microservices" is the most re-litigated argument in the industry, usually because neither side is
arguing from explicit criteria. This task asks you to make the criteria explicit before you make the
recommendation — so that the recommendation is something a mentor, or a future you, could actually check.

## Authoritative resources

- **The Twelve-Factor App** (supporting): https://12factor.net/ — relevant if a distributed option is on the
  table; several factors (statelessness, disposability, config) are exactly the properties that make a
  microservice-style option viable or not for your scenario.

Use official documentation as your primary source; if you use other material, record it in your notes.

## Work to complete

1. Take the scenario brief you used in task `sa1t1-001` (or a new one, if your mentor assigns one), along with its
   NFR budgets.
2. Compare at least three architectural options: a monolith, a microservices split, and a modular monolith (or
   another genuine third option if it fits your scenario better — state why).
3. Score all three against at least three explicit criteria drawn directly from your NFR budgets (for example:
   deployment independence needed for a specific team-scaling number, latency overhead per network hop against
   your latency budget, operational cost against a stated ceiling).
4. Write an ADR recording the recommendation, referencing the comparison, and stating explicitly what would have to
   change in the scenario for the recommendation to flip.

## Required evidence

- A written comparison scoring at least three architectural options against at least three explicit criteria drawn
  from stated NFRs
- An ADR recording the final recommendation, referencing the comparison
- A note stating which criterion most changed the outcome and why

## Acceptance criteria

- [ ] At least three architectural styles are compared against the same explicit criteria, not narrative prose
      alone.
- [ ] Each criterion is tied to a specific stated NFR or constraint from the scenario.
- [ ] The final ADR states what would have to change in the scenario for the recommendation to flip.

## Reflection

1. Which criterion most changed the outcome, and would you have guessed that before scoring?
2. What is the strongest argument for the option you rejected?

Also record: what took longer than expected, what you'd practice again, what remains unclear.

## Mentor review guide

- Change one number in the scenario (team size, growth rate, or a latency budget) and ask whether the
  recommendation still holds. A defensible comparison should make this easy to answer; a narrative-only one won't.

Suggested outcome: **Approve**, **Request revision**, or **Discuss live**.

## AI use policy

Mode: **guided**. AI may explain the trade-offs generally and quiz your understanding of them. AI must not produce
the scoring or the recommendation for your specific scenario — that judgment is the task. Disclose any material AI
use.

## Completion gate

This task is not complete when three options are listed. It is complete once the recommendation is tied to specific
numbers from your own scenario, and you can state what would flip it.
