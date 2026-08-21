# Capacity and Latency Budget Modeling

**Task ID:** `sa1t2-002`
**Estimated effort:** 8 hours
**Module:** Scalability

## Why this task exists

"It should scale fine" is not an engineering claim, it's a hope. This task asks you to build a back-of-envelope
model — the kind you'd sketch on a whiteboard in a design review — that shows its formulas, so a mentor (or you,
three months later) can check the arithmetic and challenge an assumption directly rather than arguing about vibes.

## Authoritative resources

- **Prometheus Documentation** (supporting): https://prometheus.io/docs/introduction/overview/ — useful for
  grounding what a "p99 latency" or "request rate" figure actually means as something a running system would
  report, so your model's numbers are the kind you could later validate against real metrics.

## Work to complete

1. Take the scenario and NFR budgets from `sa1t2-001` (or a new scenario if assigned), including a stated growth
   number (e.g., "5x current peak load within 18 months").
2. Build a capacity model: for each major component (API layer, database, cache, queue, and similar), derive
   expected request rate, data volume growth, and required throughput from the stated inputs — showing the formula
   for each derived number, not just the result.
3. Allocate the end-to-end latency budget from your NFRs across at least three components on the request path,
   such that the allocations sum to no more than the overall target.
4. Identify the single most likely bottleneck component, backed by a specific number from your model, and state
   one mitigation.

## Required evidence

- A capacity model document showing the formulas and input assumptions used, not just final numbers
- A latency budget table allocating the end-to-end target across at least three components
- A note identifying the single most likely bottleneck and the specific number from the model that points to it

## Acceptance criteria

- [ ] Every capacity number states its formula and input assumptions, not a bare final figure.
- [ ] The latency budget across components sums to no more than the stated end-to-end target.
- [ ] The identified bottleneck is supported by a specific number from the model, not a general intuition.

## Reflection

1. Which input assumption, if wrong, would most change your conclusion about the bottleneck?
2. What would you measure in a real running system to validate or correct this model?

Also record: what took longer than expected, what you'd practice again, what remains unclear.

## Mentor review guide

- Change one input assumption (the growth multiplier, or the read/write ratio) and ask the apprentice to recompute
  the bottleneck live. A model built on real formulas should make this tractable in minutes, not hours.

Suggested outcome: **Approve**, **Request revision**, or **Discuss live**.

## AI use policy

Mode: **guided**. AI may explain how to structure a back-of-envelope model and quiz your understanding of the
formulas. AI must not produce the model's numbers or bottleneck conclusion for your specific scenario. Disclose any
material AI use.

## Completion gate

This task is not complete when a spreadsheet of numbers exists. It is complete once you can recompute the
bottleneck live after a mentor changes one assumption.
