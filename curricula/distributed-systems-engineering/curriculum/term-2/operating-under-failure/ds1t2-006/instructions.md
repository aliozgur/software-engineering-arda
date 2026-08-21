# Operating Contract for the System You Assembled

**Task ID:** `ds1t2-006`
**Estimated effort:** 18 hours
**Module:** Operating Under Failure

## Objective

Wire together a path you already built: data owned by more than one
process (replicas or shards) **and** an asynchronous hop (outbox, Kafka,
or RabbitMQ). Write a three-class failure playbook *before* you run it.
Run all three classes. Publish an operating contract a mentor could use
without you in the room: what is refused, what is retried, what can be
lost, and which trace or query proves each case.

## Why this task exists

The rest of this curriculum isolated one mechanism at a time so a
trade-off was reproducible. This last task asks whether those mechanisms
still have a sentence you will stand behind when they share one request
path. The SWE distributed-systems term ends on paper responses, an
educational consensus lab, and a saga. You are going further: a contract
with confirmation queries, written after contact with the playbook, not
before.

LEARN BY DOING. GROW THROUGH MENTORSHIP.

## Authoritative resources

- **Apache Kafka Documentation** (reference): https://kafka.apache.org/documentation/
- **OpenTelemetry Documentation** (reference): https://opentelemetry.io/docs/
- **Docker Get Started** (reference): https://docs.docker.com/get-started/

You already have Postgres, RabbitMQ, and MIT 6.5840 notes from earlier
tasks. Reuse them. Do not start a new stack unless a previous component
is genuinely gone.

## Setup notes

- Assemble, do not rebuild. A new microservice that reimplements
  everything in one weekend is a different task and will be rejected.
- Minimum topology: two or more data-owning processes **and** one
  broker or outbox hop. Example: partitioned store → outbox → Kafka →
  consumer, or primary/replica Postgres → outbox → RabbitMQ.
- Mentorship is optional. If you have no mentor, the contract must still
  be specific enough that a stranger can execute one playbook row and
  score it.

## Work to complete

1. Write `playbook.md` **first** and commit it. Three failure classes,
   drawn from work you have already done — for example: leader partition,
   unclean or dual-write loss, reshard window, broker restart, poison
   message. For each class state:
   - how you inject it
   - expected client result (refuse / timeout / success)
   - expected durable result (row present, event present, key missing,
     offset lost, …)
   - the confirmation query (trace attribute, SQL, `GET`, consume from
     earliest)
2. Assemble the path. Keep traces from `ds1t2-005` (or re-instrument
   just enough that the confirmation queries exist).
3. Run each playbook row. Capture client output, the confirmation query
   result, and a pass/fail against both predictions. When a prediction
   is wrong, leave the mismatch in the log and **then** edit the
   contract — do not silently fix the playbook to match the run without
   a recorded mismatch.
4. Write `OPERATING_CONTRACT.md` (or a README section) as numbered
   falsifiable rules only. Required coverage:
   - a refuse-versus-timeout bound (a number)
   - a named loss case, **or** an explicit "no acked write is lost"
     together with the setting that makes that true
     (`unclean.leader.election.enable=false`, fencing on, outbox, …)
   - the telemetry signal that classifies accepted-then-lost
   Forbidden phrases as the whole rule: "highly available," "best
   effort," "eventually consistent" with no anomaly named.
5. Add a short "how to page this" paragraph: which file to open, which
   query to run, what you would not restart first.

## Evidence you'll submit

- Playbook committed before the runs (or timestamped earlier than every
  run log).
- Three captured runs with confirmation queries and pass/fail.
- The operating contract.
- Git history of assemble → playbook → runs → contract edits.
- Reflection notes.

## Acceptance criteria

- [ ] The assembled path includes (a) more than one process that owns
      data (replicas or shards) and (b) an asynchronous hop (outbox,
      Kafka, or RabbitMQ); a single process with an in-memory queue does
      not count.
- [ ] The playbook commit precedes the first run commit or the playbook
      file carries timestamps earlier than the run logs for all three
      classes.
- [ ] Each of the three captured runs includes the playbook's
      confirmation query (trace, SQL, or consume) and a pass/fail
      against the predicted client result and predicted durable result.
- [ ] The operating contract is a list of falsifiable rules that mention
      at least: refuse vs timeout bounds, a named loss case (or an
      explicit "no acked write is lost" with the setting that makes it
      true), and the telemetry signal used to classify
      accepted-then-lost.

## Reflection

Answer in your own words after doing the work:

1. Which playbook row survived contact with the assembled path, and
   which rule did you have to weaken? Quote the before and after
   sentences.
2. If a mentor paged you with only the accepted-then-lost signal from
   `ds1t2-005`, which playbook row would you run first, and what would
   you refuse to restart until you had the confirmation query?

Also record: what took longer than expected, and what remains unclear
about promising a contract versus reproducing one failure at a time.

## Mentor review guide

If a mentor reviews this work, pick one contract rule and try to break
it with a failure the playbook did not list. Approve only if the
apprentice can say whether the rule still holds or must be narrowed.
Do not approve a contract that restates CAP or names products without
settings.

Suggested review outcome: **Approve**, **Request revision**, or **Create
follow-up challenge**.

## AI use policy

Mode: **guided**. Explain, hint, and quiz are available; solution
generation is not — including not generating the contract from a
template without the runs. Disclose any material AI use with
provider/model, purpose, and how you verified each rule against a
captured run.

## Completion gate

This task is complete only after the evidence is submitted and, when a
mentor is present, the mentor approves the demonstrated competency.
A playbook you did not run is not a contract.
