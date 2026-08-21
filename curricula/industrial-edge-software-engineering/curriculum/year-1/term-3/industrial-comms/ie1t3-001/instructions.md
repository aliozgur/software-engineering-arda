# Modbus request/response you can break on purpose

**Task ID:** `ie1t3-001`
**Estimated effort:** 10 hours
**Module:** Industrial Comms

## Why this task exists

MQTT was the IT-shaped bus. Modbus is still the OT-shaped one. Function codes, exception codes, and a 16-bit register map are how a lot of real plants still move numbers. You will implement a sliver of the official application protocol over TCP on localhost so a mentor can read the hex.

Host-side C. No USB-RS485 dongle, no licensed gateway, no purchased PLC.

## Authoritative resources

- **Modbus Application Protocol Specification V1.1b3** (primary): https://www.modbus.org/docs/Modbus_Application_Protocol_V1_1b3.pdf — PDU, function 0x03 Read Holding Registers, 0x06 Write Single Register, exception 0x02 Illegal Data Address. Use a Modbus TCP ADU (MBAP + PDU) as commonly deployed; if the PDF you have is PDU-only, state the MBAP layout you used (transaction id, protocol id 0, length, unit id).

Use the official spec as the primary source. If you use additional implementation guides from modbus.org, record them.

## Work to complete

1. Implement a holding-register map of a documented size (at least 16 registers). Addresses outside that map are unmapped.
2. Server on localhost: parse MBAP + PDU. Support:
   - **0x03** Read Holding Registers (quantity 1..4 is enough if documented);
   - **0x06** Write Single Register;
   - exception **0x02** (Illegal Data Address) with exception function `function | 0x80`.
3. Client (same repo): write registers 0..3 with known values, read them back, hex-dump both request and response.
4. Client: read an unmapped address; hex-dump the exception (function `0x83`, code `0x02`).
5. For each dumped frame, write one line: `MBAP Length = <n>, remaining bytes after Length = <n>` and show they match the spec rule.
6. Property tests: generate at least 20 cases (random valid address in range, random value, write then read; plus several unmapped addresses). One command prints `passed=N` with `N >= 20`.
7. Incremental history: parser → 0x06/0x03 happy path → exception → property suite.

## Required evidence

- Server and client sources with incremental Git history
- Hex dump of a successful read of registers 0..3 after writes
- Hex dump of exception `0x83` / `0x02`
- MBAP length consistency shown for both frames
- Captured property-suite run with pass count ≥ 20
- Reflection notes answering the task questions

Submit a repository URL plus a commit reference. Do not submit only screenshots of a Modbus GUI.

## Acceptance criteria

- [ ] A client read of holding registers 0 through 3 returns the values previously written with function 0x06 (or 0x10 if you also implement it); request and response hex dumps are captured.
- [ ] A read of an address outside the implemented map returns function code 0x83 and exception code 0x02; the hex dump is captured.
- [ ] For both the success and exception frames, the MBAP Length field is consistent with the PDU size as defined in the Modbus TCP ADU (Length = remaining bytes after the Length field).
- [ ] A property or generated-case suite of at least 20 cases runs in one command; the captured output prints a pass count greater than or equal to 20.

The mentor may ask you to craft a PDU with a bad length and show the server rejects it. A library that hides the ADU with no hex dump is not enough unless you still dump the bytes on the wire (`tcpdump`/loopback capture is acceptable).

## Reflection

Answer these in your own words after doing the work:

1. Why is exception `0x02` the right answer for an unmapped address, and what would a timeout (no response) make a scanner do instead?
2. If you later put this map behind MQTT, which field is the register address analogous to, and which MQTT QoS would you pick for a single 0x06 write?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to parse the MBAP length bytes from the hex dump out loud.
- Ask what happens if quantity on 0x03 is 0 or 125 — they should cite the spec range even if they only implemented 1..4.
- Do not approve a server that returns 0x0000 for unmapped addresses instead of an exception.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
