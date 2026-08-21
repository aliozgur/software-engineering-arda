# Choosing a Data Architecture for Stated Access Patterns

**Task ID:** `sa1t2-001`
**Estimated effort:** 8 hours
**Module:** Data Architecture

## Why this task exists

Term 1 was about the shape of the system. Term 2 starts with the data underneath it, because a data architecture
decision made for the wrong reason is often the most expensive one to undo later. This task requires justifying a
storage and consistency choice against how the data is actually accessed — not against which database you already
know best.

## Authoritative resources

- **PostgreSQL Documentation** (reference): https://www.postgresql.org/docs/current/
- **MongoDB Manual** (reference): https://www.mongodb.com/docs/manual/

Use both if you're genuinely comparing relational and document models; use whichever is relevant if your scenario
points clearly one way, but say why the other was rejected.

## Work to complete

1. Take a scenario with at least four distinct access patterns stated explicitly — for example: high-frequency
   single-record lookups by key, a small number of complex multi-entity joins for reporting, bulk writes from an
   ingestion pipeline, and a search-by-attribute pattern.
2. Choose a storage architecture: a single relational store, a single document store, or a deliberate
   polyglot/mixed approach. Reject at least one option explicitly.
3. State the consistency model assumed at each service boundary that touches this data (strong, eventual, or a
   specific bounded staleness) and draw a data-flow diagram showing where each store sits.
4. Identify at least one data element that is sensitive (personal data, payment detail, credential, or similar),
   classify it, and state the specific architectural control that follows from that classification (encryption at
   rest, a stricter access boundary, a retention limit).
5. Write an ADR recording the decision.

## Required evidence

- A data-flow diagram showing where each data store sits and the consistency model assumed at each boundary
- An ADR justifying the storage choice against the stated access patterns, naming at least one rejected storage
  option
- A note classifying at least one data element as sensitive and stating the resulting architectural requirement

## Acceptance criteria

- [ ] The chosen storage model is justified against at least three concrete access patterns from the brief, not a
      general preference.
- [ ] The ADR states the consistency model assumed at each service boundary shown in the diagram.
- [ ] At least one sensitive data element is identified with a corresponding architectural control, not merely a
      mention.

## Reflection

1. Which access pattern was hardest to satisfy with your chosen storage model, and what did you give up to
   accommodate it?
2. If the bulk-ingestion pattern doubled in volume tomorrow, what part of this architecture breaks first?

Also record: what took longer than expected, what you'd practice again, what remains unclear.

## Mentor review guide

- Pick the access pattern the apprentice spent the least time on and ask them to walk through it against the
  chosen store in detail.
- Ask what happens to the sensitive-data control if the data element is later joined into a new report or export.

Suggested outcome: **Approve**, **Request revision**, or **Discuss live**.

## AI use policy

Mode: **guided**. AI may explain consistency models and storage trade-offs generally, and quiz your understanding.
AI must not choose the storage model or write the ADR's justification for your specific access patterns. Disclose
any material AI use.

## Completion gate

This task is not complete once a diagram exists. It is complete once the choice is justified against your own
stated access patterns, including the one you didn't design for first.
