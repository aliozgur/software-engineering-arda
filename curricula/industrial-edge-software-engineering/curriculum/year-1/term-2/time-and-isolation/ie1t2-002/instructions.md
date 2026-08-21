# Isolation on a real OS, then the MCU contrast

**Task ID:** `ie1t2-002`
**Estimated effort:** 8 hours
**Module:** Time and Isolation

## Why this task exists

Your cooperative scheduler shares one address space with every task. xv6 does not. This task is the honest look at what a general-purpose OS spends transistors and cycles on — processes, virtual memory, syscalls — and what a typical MCU *does not* give you unless you add an MPU and a lot of discipline.

You will boot the official MIT 6.1810 xv6 under QEMU. You are **not** required to complete a full multi-week 6.1810 lab. You are required to run the system, point at one trap/syscall path in the source, and write a contrast a mentor can mark.

Host + QEMU. No board required. If you already have a Cortex-M board, you may add an optional MPU note; it does not replace the xv6 session.

## Authoritative resources

- **MIT 6.1810 — Operating System Engineering** (primary): https://pdos.csail.mit.edu/6.1810/ — lectures on isolation, processes, and system calls; the xv6 source and the documented QEMU boot path.
- **QEMU Documentation** (reference): https://www.qemu.org/docs/master/ — system emulation invocation used by the 6.1810 Makefile.

Use the official courseware as the primary source. If you use anything else, record it. Do not submit a third-party "xv6 explained" essay in place of a session log.

## Work to complete

1. Clone or fetch the xv6 / 6.1810 tree specified by the current 6.1810 site. Build and boot it under QEMU using the 6.1810 documented target (typically `make qemu`).
2. From the xv6 shell, run a user program (a built-in or a trivial user program from the tree). Capture the console session.
3. Open the trap/syscall path in the source (names vary by year: `usertrap`, `syscall`, trampoline). Write down **file + function** you actually opened. Optional but useful: set a GDB breakpoint on that function once, or add a single temporary `printf` you then revert — capture that evidence.
4. Write `MCU-CONTRAST.md` with four rows:
   - **isolation unit** (process vs task/address space)
   - **memory protection** (page tables vs MPU / none)
   - **privileged transition** (syscall/ecall vs SVC/PendSV/interrupt)
   - **failure mode** (kill process vs hardfault / whole-node reset)
   Each row: UNIX/xv6 column + MCU/RTOS column (FreeRTOS or bare-metal Cortex-M is fine).
5. Add one paragraph: name a security property xv6 gets from virtual memory (for example, process A cannot write process B's pages) that a Cortex-M0 without an MPU does not provide.

## Required evidence

- A captured xv6-under-QEMU session showing a user process and a syscall or trap
- A source citation (file and function) for the path you exercised
- `MCU-CONTRAST.md` with the four named rows
- A paragraph on the virtual-memory security property versus Cortex-M0 without MPU
- Reflection notes answering the task questions

Submit the contrast file and the session log in a repository (or as files next to a short README). Do not submit only screenshots of the QEMU window if you can capture the console.

## Acceptance criteria

- [ ] The captured session log shows xv6 (or the official 6.1810 user environment) running under QEMU and includes a user-level command or program plus evidence of a syscall or trap.
- [ ] `MCU-CONTRAST.md` has four rows titled isolation unit, memory protection, privileged transition, and failure mode; each row has a UNIX/xv6 mechanism and a corresponding MCU or RTOS mechanism.
- [ ] `MCU-CONTRAST.md` contains a paragraph that names one security property provided by xv6 virtual memory and states that a Cortex-M0-class core without an MPU does not have that property.
- [ ] The source citation names a file and function from the 6.1810/xv6 tree, not a blog paraphrase.

The mentor may ask you to open the cited function and walk one register or stack action. A contrast written without a boot log is not enough.

## Reflection

Answer these in your own words after doing the work:

1. If your Term 2 scheduler and a network stack share RAM with no MPU, which failure mode row of your table is the one you actually shipped?
2. Name one 6.1810 idea you would *not* copy onto a 64 KiB MCU, and one you would (even in miniature).

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to point at the cited function in the tree (screen share or a pasted excerpt with line numbers).
- Ask what an MPU *could* buy on Cortex-M that their table currently lists as "none."
- Do not approve a contrast that treats FreeRTOS tasks as equivalent to xv6 processes without naming the missing MMU.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
