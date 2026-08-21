# Replicated Key-Value Store with Tunable Consistency

**Task ID:** `ds1t1-001`
**Estimated effort:** 12 hours
**Module:** Replication and Consistency

## Objective

Build a small key-value store with one leader and at least two followers, each
running as an independent OS process, communicating only over a real network
protocol (TCP, HTTP, or gRPC — your choice). The store must support two read
modes selectable per request, and you must produce a script that makes a real
consistency anomaly appear under one mode and disappear under the other,
every time it runs.

## Why this task exists

Every distributed systems conversation eventually invokes "consistency" as a
word everyone nods at and no one has actually seen fail. This task removes
the hand-waving: by the end of it you will have caused, and be able to
explain, a specific anomaly in a system you control. Every later task in this
term assumes you can distinguish "replicated" from "committed" from
"consistent," in your own system, not just in the reading.

## Setup notes

- "Separate OS processes" means separate binaries or separate invocations of
  the same binary with a role flag (`--role=leader`, `--role=follower`) —
  not goroutines/threads/tasks inside one process pretending to be nodes.
  Shared memory or a shared in-process object between "nodes" defeats the
  point of the task.
- Pick any language you're comfortable shipping a small network service in.
  Nothing here requires a specific stack.

## Work to complete

1. Implement a leader process that accepts `PUT`/`GET`, appends writes to an
   in-memory log, and asynchronously ships new entries to followers.
2. Implement at least two follower processes that receive and apply the
   leader's log entries and can serve reads.
3. Implement two read modes, selectable per request:
   - `strict` — a read is served by the leader, or by a follower that can
     prove it has applied every entry up to the leader's latest acknowledged
     offset; otherwise it is refused or forwarded.
   - `relaxed` — a read is served by whichever replica the client happens to
     hit, with no freshness check.
4. Build a reproduction script that: writes a value through the leader,
   immediately reads it back from a follower you have deliberately delayed,
   under `relaxed` mode — showing a stale or missing result — and then
   repeats the identical sequence under `strict` mode, showing the read is
   either correct or explicitly refused. Inject the delay yourself (a sleep,
   a held lock, an artificial replication lag) so the anomaly is
   deterministic — don't rely on incidental timing that might not reproduce
   on a different machine.
5. Write a `README.md` that names, for each mode, which consistency model it
   satisfies — linearizable, sequential, causal, or eventual — and ties that
   claim directly to whether the demonstrated anomaly can occur under that
   model's definition. Also state explicitly what "acknowledged" means for a
   write in your system (does the leader ack before or after shipping to
   followers? does it wait for any follower to apply?).

## Evidence you'll submit

- Git history showing the leader-only version committed before followers and
  read modes were added — this is a build-up, not a single drop.
- The reproduction script and a captured run of its output showing the
  anomaly under `relaxed` and its absence under `strict`.
- `README.md` with the named-consistency-model claims.
- Reflection notes (see below).

## Acceptance criteria

- [ ] The leader and at least two followers run as separate OS processes
      exchanging state only over a network socket protocol.
- [ ] The reproduction script deterministically reproduces the stale/missing
      read every run under relaxed mode and never under strict mode.
- [ ] README names a specific consistency model for each mode and ties the
      claim to the demonstrated anomaly, not to a general assertion.
- [ ] The write path's acknowledgment semantics are stated explicitly
      (leader-only ack vs. quorum ack).

Check each of these yourself before you submit — a mentor will check the
same four things and nothing more subjective than that.

## Reflection

Answer in your own words after doing the work:

1. What specifically had to be true about your follower for the `strict`
   read to be safe to serve there instead of forwarding to the leader?
2. If you had shipped writes to followers synchronously instead of
   asynchronously, which of the two modes would have become unnecessary, and
   why?

Also record: what took longer than expected, and what remains unclear about
the boundary between "replicated" and "consistent" in your implementation.

## AI use policy

Mode: **guided**. Explain, hint, and quiz are available; solution generation
is not — this task is meant to build the muscle you'll need for the rest of
the term, and a generated solution would skip exactly that. Disclose any
material AI use with provider/model, purpose, and how you verified the
result.
