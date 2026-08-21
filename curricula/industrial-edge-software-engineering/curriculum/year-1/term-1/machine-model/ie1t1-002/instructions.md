# Build the machine, then map it to the edge

**Task ID:** `ie1t1-002`
**Estimated effort:** 8 hours
**Module:** Machine Model

## Why this task exists

An industrial node is still a machine: registers, addressable memory, an instruction word, a clock. Nand2Tetris is the shortest honest path to a machine you built yourself. This task is not "finish a hardware project for its own sake" — it is so the next task's memory-mapped registers have a place to live in your head.

This is an apprenticeship task, not a content-consumption checkbox. The official hardware simulator and test scripts are the authority. Completion requires passing those tests and a map a mentor can check against a real MCU or QEMU machine.

No proprietary board is required. Use the official Nand2Tetris tools on the host.

## Authoritative resources

- **Nand2Tetris — Building a Modern Computer From First Principles** (primary): https://www.nand2tetris.org/ — Project 2 (ALU) and Project 3 (Memory), plus the Hack machine overview used for the fetch-decode-execute note.

Use the linked courseware as the primary source. You may use additional sources, but record them in your learning notes and prefer the official projects over third-party HDL dumps.

## Work to complete

1. Install the official Nand2Tetris software suite from the project site. Do not substitute a random GitHub "solutions" tree.
2. Complete **Project 2 (ALU)** and **Project 3 (Memory)** using the official `.hdl` chips and the official test scripts. Capture the simulator/test output that shows each project passing.
3. From the Hack CPU material (lectures / Project 5 overview — you do **not** have to finish Project 5), write a fetch-decode-execute note: three short paragraphs. Each paragraph names what is read and what is written in that step.
4. Write `EDGE-MAP.md` with five rows: **register**, **RAM**, **ROM**, **instruction word**, **clock**. For each row, name the Hack construct and the corresponding construct on one named target — a Cortex-M0/M3/M4, AVR, RISC-V `virt`, or another MCU/QEMU machine you can cite from public docs. One sentence of mechanism per row, not a synonym.
5. Commit HDL incrementally (ALU before RAM, or chip-by-chip). A single "all tests pass" commit is not enough history.

## Required evidence

- Captured official Nand2Tetris test-script output showing Project 2 and Project 3 passing
- The HDL (or official project files) committed with incremental history
- `EDGE-MAP.md` with five named rows as specified
- A written fetch-decode-execute note listing what is read and written in each step
- Reflection notes answering the task questions

Submit a repository URL plus a commit reference. Do not submit only screenshots of the hardware simulator.

## Acceptance criteria

- [ ] The official Nand2Tetris test scripts for Project 2 (ALU) and Project 3 (Memory) are shown passing in a captured log; the log names the test files.
- [ ] `EDGE-MAP.md` contains exactly five rows: register, RAM, ROM, instruction word, and clock — each row names one Hack construct and one corresponding construct on a named MCU family or QEMU machine, plus one sentence of mechanism.
- [ ] The fetch-decode-execute note lists those three steps as separate paragraphs and, for each step, names at least one location that is read and at least one location that is written.
- [ ] Git history contains at least two commits that change HDL or project files before the final passing run.

The mentor may ask you to change one chip input live and predict the test that will fail. Passing tests alone are not proof you can map the machine to an MCU.

## Reflection

Answer these in your own words after doing the work:

1. On your named MCU or QEMU target, what plays the role of Hack ROM for the program image, and what happens on that target if you try to write it at runtime?
2. Which Hack construct in your five-row map is the weakest analogy, and what does the real machine do that Hack does not?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Pick one `EDGE-MAP.md` row and ask the apprentice to defend the mechanism sentence without reading it.
- Ask what a memory-mapped I/O register is in this model — if they cannot place it relative to RAM, they are not ready for `ie1t1-003`.
- Do not approve a map that only renames Hack terms ("RAM is SRAM") with no mechanism.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

Do not paste a completed HDL solution from an AI tool or a solutions repository. The official tests are how we tell the difference.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
