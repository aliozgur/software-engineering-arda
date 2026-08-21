# Caching as an Architectural Decision, Not a Speed Hack

**Task ID:** `sa1t2-003`
**Estimated effort:** 8 hours
**Module:** Caching

## Why this task exists

Adding a cache is usually sold as a performance win. Architecturally it is a
consistency decision: you are choosing how wrong a read is allowed to be, for how
long, and who is responsible for noticing. This task asks you to treat cache
placement and invalidation as a decision you can defend against the latency and
consistency budgets you already wrote — not as a default "we'll put Redis in
front of it."

This is a judgment task. Reading about cache types is preparation. Completion
requires a comparison, an ADR, and one stale-read walkthrough with a number on
the age of the wrong value.

## Authoritative resources

- **PostgreSQL Documentation** (supporting): https://www.postgresql.org/docs/current/
  — use it to be precise about what the database already caches (shared buffers,
  prepared statements) before you add another layer, and about the isolation
  guarantee a cached read no longer has.

Use official documentation as the primary source. If you use other material,
record it in your notes.

## Work to complete

1. Take the data architecture and the latency budget from `sa1t2-001` and
   `sa1t2-002` (or a mentor-assigned brief that states both numbers). Name the
   consistency budget in one sentence — for example, "a product-price read may
   be at most 5 seconds stale."
2. Compare at least two cache placements and a no-cache option against those
   same two budgets. Fair placements include an application-local cache, a
   dedicated cache service, an HTTP/edge cache, or leaning on the database
   buffer pool and adding nothing. Score each option; do not narrate a winner
   and then invent scores to match.
3. Choose one option. Write an ADR that states the placement and the
   invalidation rule as either a TTL in seconds or a named event that drops or
   refreshes the entry. Name at least one rejected placement with a reason that
   is not "it was slower."
4. Walk through one stale-read scenario under the chosen rule: which read, which
   value would be wrong, and the maximum age of that wrong value. If the
   no-cache option won, walk through the latency miss it accepts instead, with
   the number from the budget it violates or spends.

## Required evidence

- A comparison of at least two cache placements plus a no-cache option, each
  scored against the same latency budget and consistency budget from a prior
  task
- An ADR stating the chosen placement and the invalidation or TTL rule as a
  number or an explicit invalidating event
- A note walking through one stale-read scenario that names the maximum age of
  the stale value under the chosen rule

Submit a repository URL plus a commit reference. Keep the comparison, the ADR,
and the stale-read note as separate commits or clearly separated sections so a
mentor can inspect each.

## Acceptance criteria

- [ ] At least two cache placements and a no-cache option are scored against
      the same stated latency and consistency budgets.
- [ ] The ADR states the invalidation rule as a TTL in seconds or as a named
      event that drops or refreshes the entry.
- [ ] The stale-read note names a concrete read, the value that would be wrong,
      and the maximum age of that wrong value under the chosen rule.

## Reflection

Answer in your own words after doing the work:

1. Which budget — latency or consistency — actually decided the placement, and
   would you have guessed that before scoring?
2. If the invalidation event you named never fires, what is the worst value a
   client can still read, and after how long?

Also record: what took longer than expected, what you'd practice again, what
remains unclear.

## Mentor review guide

- Change the consistency budget by an order of magnitude (5 seconds to 50
  milliseconds, or the reverse) and ask whether the placement still holds. A
  scored comparison should make this answerable in a few minutes.
- Do not approve a TTL that is a round number with no tie to a stated budget.

Suggested outcome: **Approve**, **Request revision**, or **Discuss live**.

## AI use policy

Mode: **guided**. AI may explain cache-invalidation terminology and quiz your
understanding of stale reads. AI must not score the placements or write the ADR
for your specific budgets. Disclose any material AI use, including what you
asked and how you verified the answer.

## Completion gate

This task is not complete when a cache appears on a diagram. It is complete
once you can state, without checking your notes, the maximum age of a wrong
read under the rule you chose.
