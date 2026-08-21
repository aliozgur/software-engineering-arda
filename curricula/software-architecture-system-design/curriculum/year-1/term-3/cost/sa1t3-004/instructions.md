# Defending a Design Against a Budget Cut

**Task ID:** `sa1t3-004`
**Estimated effort:** 8 hours
**Module:** Cost

## Why this task exists

Every prior task treated a number as load-bearing — latency, RPO, an error
budget. Cost is the number that usually arrives last and then overrules the
others. This task asks you to put formulas on the cost of a design you already
defended, take a stated cut, revise the ADR, and explain the user-visible
impact to someone who will not read a topology diagram. That last artifact is
professional practice: if you cannot say what the user will notice, you have
not finished the trade-off.

This is not a procurement exercise. You may use round unit prices you state
as assumptions. The arithmetic and the revision are the work.

## Authoritative resources

- **Prometheus Documentation** (supporting): https://prometheus.io/docs/introduction/overview/
  — useful for grounding a cost driver in something you would later measure
  (request rate, stored series, sample volume). You are not required to run
  Prometheus; you are required to name drivers a metric could later validate.

Use official documentation as the primary source. If you use other material,
record it in your notes.

## Work to complete

1. Take a prior design that has a capacity model or a multi-region topology
   (`sa1t2-002` or `sa1t3-003`). List at least three cost drivers — compute
   hours, stored gigabytes, egress, replica count times instance cost, queued
   messages. For each, write a formula and a unit. State unit prices as
   explicit assumptions.
2. Apply a budget cut. Use 40% unless a mentor assigns a different
   percentage. Recompute. Name what you will drop or defer: a region, a
   replica, a cache tier, an active-active write path, a freshness target.
3. Write a superseding or amended ADR against a specific prior decision.
   Name the percentage, name what was dropped, and state which NFR or SLO
   is now worse, with the number.
4. Write a stakeholder note of at most 400 words. One sentence in it must
   state the user-visible impact and must contain no cloud, queue, or
   datastore product name. "Checkout will take up to two seconds longer
   during a regional outage" is the shape; "we will drop the secondary
   Aurora cluster" is not.

## Required evidence

- A cost model showing a formula and a unit for at least three cost drivers
  derived from a prior capacity or topology decision
- A superseding or amended ADR that responds to a stated percentage budget
  cut and names what was dropped or deferred
- A stakeholder note of at most 400 words that names the user-visible impact
  of the cut in one sentence containing no cloud or datastore product name

Submit a repository URL plus a commit reference. Keep the pre-cut and
post-cut models in history.

## Acceptance criteria

- [ ] The cost model states a formula and a unit for at least three drivers.
- [ ] A second ADR marks a prior decision as superseded or amended, names the
      percentage cut, and names at least one capability or region or replica
      that was dropped.
- [ ] The stakeholder note is at most 400 words and contains one sentence
      that states the user-visible impact without naming a cloud, queue, or
      datastore product.

## Reflection

1. Which cost driver, if your unit-price assumption were 3x wrong, would
   change the drop you chose?
2. What did you have to leave out of the stakeholder note that a mentor
   still needs to see in the ADR?

Also record: what took longer than expected, what you'd practice again, what
remains unclear.

## Mentor review guide

- Change the cut from 40% to 15% (or the reverse) and ask whether the same
  drop is still the right one. A formula-backed model should make this a
  short conversation.
- Read only the stakeholder note first. If you cannot tell what the user
  will notice, request revision before opening the ADR.

Suggested outcome: **Approve**, **Request revision**, or **Discuss live**.

## AI use policy

Mode: **guided**. AI may explain how to structure a cost model and quiz your
understanding of the drivers. AI must not produce the post-cut drop or write
the stakeholder sentence for your specific design. Disclose any material AI
use.

## Completion gate

This task is not complete when a spreadsheet of costs exists. It is complete
once a mentor can read the stakeholder sentence and know what the user will
notice, then open the ADR and see the number that forced it.
