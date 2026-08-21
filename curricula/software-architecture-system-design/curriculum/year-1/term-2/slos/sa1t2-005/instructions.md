# SLOs and Error Budgets as Design Constraints

**Task ID:** `sa1t2-005`
**Estimated effort:** 8 hours
**Module:** SLOs

## Why this task exists

The NFR sheet from term 1 and the capacity model from `sa1t2-002` gave you
targets. This task turns those targets into SLIs a running system could
actually report, then into an error budget — the quantity of failure you are
willing to spend in a stated window. That quantity is a design constraint: it
is what lets you forbid a launch, a migration, or a relaxed timeout with
arithmetic instead of opinion. This curriculum does not ask you to implement
a metrics stack; it asks you to write numbers a later instrumentation task
could be held to.

Reading about SLOs is preparation. Completion requires formulas, a computed
budget, and one change you can show the budget would not survive.

## Authoritative resources

- **Prometheus Documentation** (primary): https://prometheus.io/docs/introduction/overview/
  — read enough to write an SLI as something a counter or histogram could
  express (a ratio of successful requests, a percentile of a latency
  histogram). You are not required to run Prometheus.

Use official documentation as the primary source. If you use other material,
record it in your notes.

## Work to complete

1. Take at least two NFR budgets from `sa1t1-001` or a later revision (latency
   and availability are the usual pair; a freshness or correctness budget is
   also fair). Rewrite each as an SLI: a formula over named events or samples,
   plus a target and a time window (for example, 30 days).
2. Compute the error budget for one SLO over that window. Show the formula.
   The result must be a quantity — failed requests at a stated offered load,
   or unavailable minutes — not a restated percentage.
3. Pick one concrete change that would spend more than the remaining budget in
   that window: a feature launch expected to add a stated error rate, a
   migration with a stated cutover outage, or a timeout relaxation that moves
   a stated share of requests past the latency SLI. Show the arithmetic.
4. Write a short note tying the SLO back to one prior architecture decision
   (`sa1t1-003`, `sa1t2-001`, `sa1t2-003`, or `sa1t2-004`). State which
   decision you would freeze or reverse while the budget is exhausted.

## Required evidence

- An SLO sheet with at least two SLIs, each written as a measurement formula
  plus a target number and a time window
- An error-budget calculation for one of those SLOs over a stated window,
  showing the formula and the resulting allowed-failure quantity
- A note naming one concrete change that would consume more than the remaining
  budget in that window, with the arithmetic

Submit a repository URL plus a commit reference. Keep the first-draft SLI
formulas and the revised versions in history if a formula changed after you
tried to compute the budget.

## Acceptance criteria

- [ ] Each of at least two SLIs is a ratio or measurement formula with named
      events or samples, not an adjective.
- [ ] The error budget is computed from the SLO target and a stated time
      window, and the result is a quantity, not a restated percentage.
- [ ] The forbidden-change note names a specific change and shows arithmetic
      that the remaining budget for that window would be exceeded.

## Reflection

1. Which SLI was hardest to write as a formula, and what event did you almost
   leave unnamed?
2. If a stakeholder wanted the SLO one nine tighter, which prior architecture
   decision would you reopen first?

Also record: what took longer than expected, what you'd practice again, what
remains unclear.

## Mentor review guide

- Change the offered load used in the budget quantity and ask the apprentice
  to recompute live. A formula-backed budget should take minutes, not a
  rewrite.
- Do not approve an SLI that cannot name the event in the denominator.

Suggested outcome: **Approve**, **Request revision**, or **Discuss live**.

## AI use policy

Mode: **guided**. AI may explain SLI/SLO terminology and quiz your
understanding of error budgets. AI must not write the formulas or the
forbidden-change arithmetic for your specific NFRs. Disclose any material AI
use.

## Completion gate

This task is not complete when two percentages appear on a slide. It is
complete once you can recompute the remaining budget after a mentor changes
the offered load or the window, and name the change you would refuse.
