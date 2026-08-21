# Choosing Between Request/Response and Event-Driven Communication

**Task ID:** `sa1t1-004`
**Estimated effort:** 7 hours
**Module:** Styles

## Why this task exists

Synchronous request/response and asynchronous event-driven communication fail differently, and the failure mode is
often the real reason to choose one over the other — not throughput. This task asks you to model both for the same
workflow and commit, in writing, to the delivery-guarantee assumption you're making. That assumption is exactly the
kind of thing that goes unstated until an incident forces the question.

## Authoritative resources

- **Apache Kafka Documentation** (supporting): https://kafka.apache.org/documentation/ — read enough to be precise
  about what "at-least-once" and consumer-group ordering actually guarantee, even if your scenario doesn't use
  Kafka specifically.

## Work to complete

1. Take a workflow with multiple downstream consumers of one event — for example, an order placement that must
   update inventory, trigger a payment capture, and notify a shipping system.
2. Model the workflow as synchronous request/response: draw the sequence, and identify what happens to the whole
   workflow when one downstream call fails or times out.
3. Model the same workflow as event-driven: draw the flow, and identify the ordering and delivery-guarantee
   assumption each consumer must make.
4. Write an ADR choosing one style for this workflow, stating the delivery-guarantee assumption explicitly, and
   walk through one concrete failure scenario for the style you rejected — a scenario that could plausibly happen,
   not a strawman.

## Required evidence

- Two sequence or flow diagrams, one per communication style, modeling the same workflow end to end
- An ADR naming the ordering and delivery-guarantee assumption made for the chosen style
- A note walking through at least one concrete failure scenario for the rejected style and why it was rejected

## Acceptance criteria

- [ ] Both diagrams model the same workflow end to end, not two different scopes.
- [ ] The ADR explicitly states the delivery-guarantee assumption for the chosen style.
- [ ] At least one concrete failure scenario is walked through for the rejected style, explaining why it was
      rejected rather than merely less preferred.

## Reflection

1. What operational cost does the style you rejected avoid, and what does your chosen style now owe you in return
   (retries, idempotency, dead-letter handling)?
2. If you had to support the rejected style's failure scenario anyway, would your recommendation still hold?

Also record: what took longer than expected, what you'd practice again, what remains unclear.

## Mentor review guide

- Ask what happens if a duplicate event is delivered, or a request is retried after a timeout whose original call
  actually succeeded. A vague answer here is a sign the delivery-guarantee assumption wasn't really thought
  through.

Suggested outcome: **Approve**, **Request revision**, or **Discuss live**.

## AI use policy

Mode: **guided**. AI may explain delivery-guarantee terminology and quiz your understanding of it. AI must not
produce the diagrams or the ADR's decision for your specific workflow. Disclose any material AI use.

## Completion gate

This task is not complete when two diagrams exist. It is complete once you can state, without checking your notes,
exactly what happens to a duplicate or lost message under your chosen style.
