# Reliable frames over a lossy simulated link

**Task ID:** `ie1t2-004`
**Estimated effort:** 10 hours
**Module:** Industrial Comms

## Why this task exists

MQTT QoS and Modbus retries will look like magic if you have never implemented a sequence number and a timer. Stanford CS144 builds a full TCP; you will not. You will take the *reliable byte stream* idea — sequence space, ACK, retransmission — and run it over a datagram you can drop on purpose.

Host-side C over a loopback UDP socket or an in-process queue with a dropper. No cloud broker, no board.

## Authoritative resources

- **Stanford CS144 — Introduction to Computer Networking** (primary): https://cs144.github.io/ — reliable transport / TCP lab lectures and write-ups. Read the reliable-byte-stream material; implement a scoped sliver, not the full lab.

Use the official courseware as the primary source. If you use anything else (RFC 793 excerpts, your own notes), record it.

## Work to complete

1. Read the CS144 material on reliable transport (sequence numbers, cumulative ACK, retransmission timer). Write `README.md` naming **one idea you will implement** and **one you will omit** (congestion control, flow control window, connection handshake — pick an omission).
2. Implement a lossy datagram: each packet is dropped with probability ≥ 0.20 (or a deterministic 1-in-5 drop). Put the fraction in `loss.conf` or similar. Optional: reorder a documented subset.
3. Implement sender and receiver:
   - **stop-and-wait** (one outstanding segment) **or** **go-back-N** with a window you document;
   - sequence numbers on data;
   - ACKs;
   - a retransmission timer (tick from `ie1t2-001` style, or `alarm`/`timerfd`).
4. Transfer at least 10 KiB of known data (a file or a generated pattern). Receiver writes the payload; show `sha256sum` (or equivalent) match with the source.
5. Log `send seq=`, `recv seq=`, `ack=`, `retransmit seq=`. The log must contain at least one retransmission.
6. Incremental history: lossy link → stop-and-wait without loss → loss + retransmit → 10 KiB check.

## Required evidence

- A loss config file stating the drop fraction (≥ 20%)
- Sender/receiver sources with incremental Git history
- A captured 10 KiB+ byte-identical transfer under that loss
- A sequence/ACK log showing at least one retransmission
- README naming one CS144 idea used and one omitted
- Reflection notes answering the task questions

Submit a repository URL plus a commit reference. Do not submit only screenshots of code.

## Acceptance criteria

- [ ] The lossy link drops at least 20 percent of datagrams as configured in a file the run reads; that file is in the repository.
- [ ] A 10 KiB or larger payload arrives byte-identical on the receiver under that loss; a checksum or diff is captured.
- [ ] The sequence/ACK log contains at least one line that shows a retransmission (same sequence number sent more than once, or an ACK gap followed by a resend).
- [ ] README names at least one CS144 reliable-transport idea that was implemented and one that was omitted.

The mentor may drop the link to 50% live and ask whether the transfer still completes (it should, slower). A transfer that only works at 0% loss is a fail.

## Reflection

Answer these in your own words after doing the work:

1. If you omitted congestion control, what happens to your sender when the drop rate rises to 50%, and is that acceptable on a 1200-baud serial plant link?
2. How would you map your sequence number to an MQTT packet identifier or a Modbus transaction id — what is the same, and what is not?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to point at the first retransmit in the log and the ACK that was missing.
- Ask what duplicate data the receiver must ignore — if they have no duplicate detection, request revision.
- Do not approve a design that ACKs in the same unreliable datagram path with no timeout.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
