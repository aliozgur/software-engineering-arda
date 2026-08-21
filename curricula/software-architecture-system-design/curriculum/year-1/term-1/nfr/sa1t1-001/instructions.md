# Turning Vague Requirements into Measurable NFR Budgets

**Task ID:** `sa1t1-001`
**Estimated effort:** 6 hours
**Module:** NFR

## Why this task exists

Almost every architecture conversation starts with adjectives: the system should be "fast," "reliable," "able to
scale." None of those can be designed against. This task is about converting a realistic brief into numbers you and
a mentor could later hold a design accountable to — a p99 latency figure, an availability percentage, a maximum
acceptable data-loss window, a peak throughput number. Every later task in this curriculum will ask you to justify a
decision against a stated NFR; this task is where those numbers first get written down honestly, including the
parts you had to assume.

This is a judgment task, not a research report. Reading about NFRs is preparation, not completion. Completion
requires a sheet of quantified budgets you can defend, including why each number is what it is.

## Scenario

Choose one of the following, or substitute a real system you have direct knowledge of (state which you used):

- A retail order-and-checkout system currently handling ~200 orders/minute at peak, expected to grow.
- An internal analytics dashboard used by ~150 employees, refreshed from batch and near-real-time sources.
- A notification/alerting service that fans a single event out to email, SMS, and push.

If you substitute a real system, keep the brief's ambiguity — don't just paste numbers from a spec you already have
memorized; show the reasoning.

## Work to complete

1. Identify at least five candidate non-functional requirements for the scenario (latency, availability, durability,
   consistency, throughput, cost ceiling, recovery time, and similar are all fair game).
2. Select at least four of them and give each a quantified budget: a specific number, not a range of adjectives.
3. For each budget, state where the number came from — a public benchmark for a comparable system, an explicit
   assumption you are making and flagging as such, or a stakeholder constraint you are told to assume.
4. After the first draft, revisit at least one budget and revise it — because a source contradicted your first
   guess, because two budgets turned out to be in tension, or because a number you assumed turned out to be
   unrealistic. Commit the revision separately from the first draft so the change is visible in history.

## Required evidence

- An NFR sheet naming at least four distinct quality attributes, each with a quantified target and a stated source
  or assumption for that number
- Git history showing the sheet was revised at least once, with a commit message or note stating what changed the
  number and why
- A short note naming which NFR was hardest to quantify and how the final number was chosen

Submit a repository URL plus a commit reference. Do not submit a single final file with no history behind it — the
revision is part of what is being assessed.

## Acceptance criteria

- [ ] At least four distinct non-functional requirements are each stated as a measurable number, not an adjective.
- [ ] Each budget names the source or reasoning used to arrive at that number.
- [ ] The revision history shows at least one budget changed after the first draft, with a note stating why.

## Reflection

Answer in your own words after doing the work:

1. Which NFR was hardest to turn into a number, and why?
2. If a stakeholder pushed back on one of your numbers tomorrow, which one would you have the weakest defense for?

Also record: what took longer than expected, what you'd do differently next time, and what remains unclear.

## Mentor review guide

- Pick one budget and ask "what happens to the design if this number were 10x smaller?" Listen for whether the
  apprentice treats the number as load-bearing or decorative.
- Do not approve a sheet where every number looks suspiciously round with no stated source.

Suggested outcome: **Approve**, **Request revision**, or **Discuss live**.

## AI use policy

Mode: **guided**. AI may explain concepts, offer hints, and quiz your understanding of what makes an NFR
measurable. AI must not generate the budgets or their sources for you — the sourcing and the judgment behind each
number is the point of the task. Disclose any material AI use, including what you asked and how you verified the
answer.

## Completion gate

This task is not complete when the sheet looks plausible. It is complete once you can explain, unprompted, where
every number came from and what would have to change for it to be wrong.
