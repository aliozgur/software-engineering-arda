# SLOs and Error Budgets You Can Actually Burn

**Task ID:** `ob1t1-004`
**Estimated effort:** 8 hours
**Module:** SLOs

## Why this task exists

Dashboards from `ob1t1-002` tell you what happened. An SLO tells you whether that was
acceptable. This task is where you turn existing RED metrics into SLIs, write an SLO
you can defend, and prove the error budget is a real number — by burning it on purpose.

An SLO you never recompute after a failure is decoration. The work is the before/after
budget, and the one sentence about what you would stop doing if the budget hit zero.

## Authoritative resources

- **Site Reliability Engineering (Google SRE Book)** (primary):
  https://sre.google/sre-book/service-level-objectives/ — Chapter 4, Service Level
  Objectives. Read SLI / SLO / SLA distinctions and the error-budget idea before you
  write numbers.
- **Prometheus Documentation** (reference): https://prometheus.io/docs/introduction/overview/
  — you will express SLIs as PromQL (or an equivalent query language) over the metrics
  you already expose.

The SRE book is published free online (CC BY-NC-ND 4.0). Prefer it over blog summaries
of "what an SLO is."

## Work to complete

1. Pick one user-facing operation from the service you instrumented in `ob1t1-002` /
   `ob1t1-003`. You may add no new metrics unless an existing series cannot express a
   ratio — if you add one, say why the old set was insufficient.
2. Write two SLIs as named queries that return a ratio or percentage:
   - **Availability** (successful requests / valid requests over a window).
   - **Latency** (requests faster than a threshold / valid requests, or an equivalent
     good-events definition — not a bare p99 standing alone without a "good" definition).
3. Set an SLO for each SLI: a target percentage and a time window (7 days is enough for
   this task; 30 days is fine if your scrape history supports it). Write where each
   target came from — a comparable public number, a constraint you are told to assume,
   or an explicit guess you flag as a guess. Round numbers with no source are not done.
4. Compute remaining error budget at a healthy baseline. Record the query and the
   numeric remaining budget (absolute failed-request allowance left, or remaining
   fraction — pick one definition and use it in both captures).
5. Induce a failure or added latency that burns the budget (forced 5xx, injected delay
   past your latency threshold, or both). Recompute. The remaining budget must be a
   strictly smaller number than the baseline.
6. Write a one-page SLO document: SLI definitions, SLO targets and windows, current
   remaining budget (both captures), and **one concrete action** you would block or
   allow if remaining budget reached zero (for example "freeze non-SLO feature deploys"
   or "page and stop the load test"). That action must be something a human could do
   the same day, not "improve reliability."

## Required evidence

- An SLO document with SLI formulas, targets, windows, and a sourced justification for
  each target
- The PromQL (or equivalent) used to compute each SLI and the remaining error budget
- Captured SLI and remaining-budget output at a healthy baseline, with numeric remaining
  budget
- Captured SLI and remaining-budget output after an induced failure, showing a strictly
  smaller remaining budget
- Reflection notes answering the questions below

Submit a repository URL plus a commit reference. Put query output in files, not only
screenshots. If a screenshot is the only way to show a UI, include the raw query result
alongside it.

## Acceptance criteria

- [ ] Each of the two SLIs is expressed as a named query that returns a ratio or
      percentage, not a raw count.
- [ ] Each SLO names a target percentage and a time window (for example 99.5 percent
      over 7 days).
- [ ] The after-failure remaining error budget is a number strictly less than the
      baseline remaining budget, shown in captured query output.
- [ ] The SLO document names one concrete action that would be blocked or allowed if
      remaining budget reached zero.

The mentor may change your latency threshold by 20% and ask you to recompute the latency
SLI live. If you are working without a mentor, do that recomputation yourself and record
whether the after-failure capture still burns the budget.

## Reflection

Answer these in your own words after doing the work:

1. If a product owner asked to tighten the availability SLO by one nine, what would
   that do to the remaining budget on the after-failure capture — show the arithmetic.
2. Which of the two SLIs would you trust less on a Monday morning, and what missing
   event would make it lie?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you learned the objective?

## Mentor review guide

Mentorship is optional. When a mentor is present: refuse an SLO whose only justification
is "99.9% is industry standard" with no source. Ask what deploy they would block if the
budget were already spent.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may explain SLI/SLO vocabulary, hint at PromQL shape, and quiz you on error-budget
arithmetic. AI must not invent your targets or write the SLO document for you — the
numbers and the zero-budget action are the point. Disclose material AI use: provider
or model if known, purpose, and how you verified the query results.

## Completion gate

This task is not complete when the document looks like an SRE template. It is complete
once both captures exist, the budget shrank, and you can defend the zero-budget action
without reading the template back.
