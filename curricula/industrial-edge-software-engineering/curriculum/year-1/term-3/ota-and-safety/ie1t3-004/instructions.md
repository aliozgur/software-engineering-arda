# Authenticated telemetry under a latency and memory budget

**Task ID:** `ie1t3-004`
**Estimated effort:** 8 hours
**Module:** OTA and Safety

## Why this task exists

You can refuse a bad firmware image. The plant still believes every MQTT or Modbus-shaped number you send. This last task adds a MAC (or AEAD) to a telemetry record, a replay window, and a **budget** — because on a constrained node, authentication that blows the stack is a different outage.

Host-side C. Mbed TLS is the suggested library because it is the usual constrained-crypto toolkit; a host HMAC from a documented API is acceptable if you still measure it. You may publish the authenticated record over the localhost MQTT path from `ie1t2-005`; that is optional. No cloud KMS.

## Authoritative resources

- **Mbed TLS Documentation** (reference): https://mbed-tls.readthedocs.io/en/latest/ — HMAC / message-authentication APIs suitable for a small record.
- **MQTT Version 5.0 (OASIS Standard)** (reference): https://docs.oasis-open.org/mqtt/mqtt/v5.0/os/mqtt-v5.0-os.html — optional if you attach the MAC to a PUBLISH payload; QoS does **not** replace the MAC.

Use official documentation as the primary source. If you use RFC 2104 (HMAC) as the algorithm note, record it.

## Work to complete

1. Write `MEASURE.md` **first**: extra-RAM budget for key material + replay window (pick a number, for example ≤ 2048 bytes); a per-record verify-time budget on the host (for example ≤ 1 ms average — you choose, you defend).
2. Record format: sequence number (or nonce), payload, MAC. Key is a compile-time or file-loaded secret (document that it is a lab key).
3. Receiver: verify MAC; reject `reject-mac`. Accept sequence only if it is unused inside a documented window (bitmap, last-N set, or strictly increasing — name it); reject `reject-replay`.
4. Tests: one bad MAC; one replay of an accepted record. Capture both.
5. Measure 1000 records: average verify time (state `clock_gettime` or equivalent) and extra RAM (key bytes + window structure; `sizeof` and a note, or a map excerpt). Compare to an unsigned path (same payload, no MAC). Write the numbers in `MEASURE.md`. They must fit the budget you wrote in step 1, or you must change the design and explain the revision in history.
6. Incremental history: budget → MAC reject → replay reject → measurement.

## Required evidence

- Telemetry auth sources with incremental Git history
- Captured bad-MAC reject
- Captured replay reject
- `MEASURE.md` with per-record verify time, extra RAM vs unsigned, N=1000
- Extra-RAM budget that the measurement does not exceed
- Reflection notes answering the task questions

Submit a repository URL plus a commit reference. Do not submit only screenshots of code.

## Acceptance criteria

- [ ] A record whose MAC does not verify is rejected; the test output names `reject-mac` or an equivalent documented code.
- [ ] Replaying a previously accepted record (same sequence number or nonce) is rejected; the test output names `reject-replay` or equivalent.
- [ ] `MEASURE.md` reports a numeric per-record verify time (milliseconds or nanoseconds, with the clock used) and extra RAM in bytes versus the unsigned path, both measured over 1000 records.
- [ ] `MEASURE.md` states an extra-RAM budget in bytes for keys plus the replay window; the measured extra RAM is less than or equal to that budget.

The mentor may ask you to shrink the window by half and say what replay becomes possible. A TLS "we would turn it on in production" paragraph without a MAC test is a fail.

## Reflection

Answer these in your own words after doing the work:

1. If verify time doubled on the target MCU (not the host), which Term 2 deadline would you renegotiate first, and using which measurement from `ie1t2-001`?
2. Does MQTT QoS 1 change your replay window, or is the MAC sequence a different layer — defend one sentence with a spec term.

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Check that `MEASURE.md` was not written after a single lucky run — ask which clock and how they averaged.
- Ask what happens at sequence wrap (uint16 vs uint32) — if they have no answer, request a note, not necessarily code.
- Do not approve extra RAM that "doesn't count" the key because it is in `.rodata`.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
