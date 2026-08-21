# Handle Late and Out-of-Order Events on Purpose

**Task ID:** `de1t2-004`
**Estimated effort:** 8 hours
**Module:** Streaming

## Why this task exists

The previous task made the sink safe under retry. This task makes the
window safe under time. Events arrive late. They also arrive out of
order. If you bucket by "when the consumer ran," you will "correct"
yesterday after it was published.

You will choose a policy for lateness and demonstrate it. Silence is not
a policy.

## Authoritative resources

- **Apache Kafka Documentation** (reference): https://kafka.apache.org/documentation/
  — treat the log as an unordered-by-event-time transport unless you
  imposed order. Event time lives in the payload.
- **PostgreSQL Documentation** (reference): https://www.postgresql.org/docs/current/
  — upserts into a window table, `late_events`, timestamps.

Use official documentation as the primary source. If you use anything else,
record it in your notes. You may keep the consumer from `de1t2-003` or
drive the same logic from a fixture file if the broker is in the way;
the clock rules must still run on a real write path.

## Work to complete

1. Give every event an `event_time` (when it happened) and a
   `processing_time` (when you ingested it). Choose a window size (one
   minute or one hour) and write it down.
2. Choose an allowed lateness (for example ten minutes). Write the
   policy for events that miss it: update the closed window anyway, or
   write to `late_events` and leave the published measure unchanged.
3. Send a happy in-order sequence so windows close (or would close) with
   a known measure.
4. Send an out-of-order event whose `event_time` is still inside an
   open or still-allowed window, but whose `processing_time` is later.
   The measure for the *event-time* window must change; the processing-time
   window must not steal it.
5. Send ten events that belong to a window that is past allowed
   lateness. Apply the written policy. Capture the closed-window measure
   and, if you chose `late_events`, those ten rows.

## Required evidence

- The window size, event-time field, and allowed-lateness value in code
  or config
- A captured event whose `processing_time` is in window B and
  `event_time` is in window A, landing in A
- The late-event policy note and the fate of the ten injected late
  events
- Before and after measures for an out-of-order event inside allowed
  lateness
- A closed-window measure that matches the written policy after a
  beyond-lateness event
- Reflection notes answering the questions below

Submit a repository URL plus a commit reference.

## Acceptance criteria

- [ ] Window assignment uses `event_time`, not `processing_time`, shown
      by an event whose `processing_time` is in window B but
      `event_time` is in window A landing in A.
- [ ] All ten late events appear either as updates to their original
      window measures or as rows in a `late_events` table or file, and
      the chosen policy is named in a note.
- [ ] An out-of-order event inside the allowed-lateness window is
      included in that window's measure, shown by captured before and
      after values.
- [ ] An event beyond allowed lateness does not silently change a closed
      window unless the written policy says it does — the captured
      measure matches the policy.

The mentor may give you a timestamp pair and ask which window and whether
it is late, before you run code. If you need to execute to know, the
policy is not written clearly enough.

## Reflection

Answer these in your own words after doing the work:

1. What consumer-facing number becomes unstable if you keep updating
   closed windows forever?
2. What do you tell an analyst who wants "the true total including
   everything that ever arrived late"?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you learned the objective?

## Mentor review guide

Ask the apprentice to draw event time versus processing time for one late
event. Do not approve grouping by `NOW()` or insert time alone.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is
not the intended path for this task. The apprentice must be able to
classify a timestamp pair without the model. Material AI assistance must
be recorded in the submission notes with the provider/model (if known),
purpose, and verification performed.

## Completion gate

This task is not complete when windows exist. It is complete once the
event-time assignment, the in-window out-of-order update, and the
beyond-lateness policy demonstration are submitted and the mentor
approves the demonstrated competency.
