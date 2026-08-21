# Memory-mapped registers you can poke from a host

**Task ID:** `ie1t1-003`
**Estimated effort:** 8 hours
**Module:** Machine Model

## Why this task exists

The last task gave you a machine. This one gives that machine peripherals: addresses that do things when you touch them. Endianness and alignment are not style choices on a Modbus map or an MCU UART. They are bugs you can ship to a plant.

Implement the device as host-side C — a byte array plus accessors — so a mentor can run the poke program without a board. Optional: the same register layout can later be driven from QEMU user-mode or a board you already own. Do not buy hardware.

## Authoritative resources

- **Nand2Tetris** (reference): https://www.nand2tetris.org/ — reuse your `EDGE-MAP.md` mental model: RAM versus something that sits on the bus and has side effects.
- **QEMU Documentation** (reference): https://www.qemu.org/docs/master/ — optional if you want to run the same binary under user-mode emulation; not required to pass the task.

Use official documentation as the primary source. If you use anything else, record it in your notes.

## Work to complete

1. Implement a 256-byte, byte-addressable device window in C. Registers:
   - `0x00` **STATUS** — 32-bit, read-only. Initialize to a documented non-zero value.
   - `0x04` **CTRL** — 32-bit, read/write.
   - `0x08` **DATA** — 32-bit, read/write.
   - `0x0C` **COUNT** — 32-bit, read-only. Increment by 1 on each successful write to DATA.
2. Provide 8-bit, 16-bit, and 32-bit accessors in both little-endian and big-endian variants. 16- and 32-bit accesses must be aligned to their size; an unaligned 32-bit access at `0x09` must fail with a documented error (enum, return code, or `errno`-style), not assemble a value from mixed bytes.
3. Write a host poke program (same repo) that:
   - writes DATA and prints COUNT before and after;
   - writes STATUS and prints STATUS before and after;
   - writes `0x01020304` via LE and via BE into DATA (reset the window between the two) and hex-dumps the four bytes;
   - attempts an unaligned 32-bit read at `0x09` and prints the error.
4. Capture the poke program's output as a file (`poke.log` or similar). Commit the implementation in at least two steps (window + accessors first, then side effects / tests).

## Required evidence

- C sources for the device window and the poke program, with incremental Git history
- A captured test run showing DATA write incrementing COUNT by 1
- A captured test run showing a write to STATUS leaving STATUS unchanged
- A captured dump of the four DATA bytes for `0x01020304` under both LE and BE 32-bit accessors
- A captured unaligned 32-bit access at `0x09` returning the documented error
- Reflection notes answering the task questions

Submit a repository URL plus a commit reference. Do not submit only screenshots of code.

## Acceptance criteria

- [ ] The device window is 256 bytes, byte-addressable, and exposes STATUS at 0x00 (read-only), CTRL at 0x04 (read/write), DATA at 0x08 (read/write), and COUNT at 0x0C (read-only, increments by 1 on each successful DATA write).
- [ ] A write of `0x01020304` through the little-endian 32-bit accessor at DATA and a write of the same value through the big-endian 32-bit accessor produce two different 4-byte sequences in the window; both sequences are captured.
- [ ] A write to offset 0x00 does not change the STATUS bytes; before and after dumps are captured.
- [ ] An unaligned 32-bit read or write at offset 0x09 returns a documented error code or result and does not store or return a silently assembled 32-bit value.

The mentor may ask you to add a fifth register live or to predict the byte sequence for `0xAABBCCDD` under BE. A green compile is not enough.

## Reflection

Answer these in your own words after doing the work:

1. If a PLC documented a holding register as "32-bit big-endian at address 0x08," which of your accessors must the host use, and what bug would the other accessor hide?
2. Why is a silent unaligned 32-bit read more dangerous on a memory-mapped peripheral than on a normal C array of `uint32_t`?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to hex-dump DATA after an LE write of `0x01020304` without looking at the log.
- Ask whether COUNT should increment on a failed (unaligned) DATA write — the submitted policy must be consistent with the code.
- Do not approve if endianness was implemented by `#ifdef` on the host only, with no explicit LE/BE accessors.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
