# Budget every byte: static allocation, firmware style

**Task ID:** `ie1t1-001`
**Estimated effort:** 8 hours
**Module:** Constrained Memory

## Why this task exists

On a plant-floor node, RAM is a budget, not a suggestion. A general-purpose heap that "usually fits" is how firmware dies at 3 a.m. after a week of uptime. This task is where you learn to write C the way the rest of this curriculum expects: every byte accounted for, no `malloc`, and a measurement that a mentor can open.

This is an apprenticeship task, not a content-consumption checkbox. Reading linker documentation is only preparation. Completion requires evidence that you can apply and explain the ideas.

Prefer host-side C with GCC or Clang. QEMU or a well-documented MCU board you already own is optional and never required. Do not buy hardware for this task.

## Authoritative resources

- **GNU Linker (ld) Documentation** (reference): https://sourceware.org/binutils/docs/ld/ — use this for map files, section names (`.text`, `.data`, `.bss`), and how the linker reports sizes.

Use the linked documentation as the primary source. You may use additional sources, but record them in your learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Create a repository and write `MEMORY.md` **before** you implement the store. State a numeric budget in bytes for `.text`, `.data`, `.bss`, and stack, and a total RAM cap of at most 64 KiB for `.data + .bss + stack`. Commit this file first.
2. Implement a fixed-capacity telemetry store in C: a compile-time constant `N` records, each a fixed struct (timestamp, sensor id, value). All storage is static or caller-provided. No heap.
3. Build with a documented host toolchain (GCC or Clang). Produce a `size` report or a linker map (`-Wl,-Map=store.map` or the Clang equivalent) and save the output as a file in the repository.
4. Add a gate that fails the build if `malloc`, `calloc`, `realloc`, or `free` appears in the C sources (a small script, a `#define malloc(...)` `#error`, or a CI grep). Then, on a disposable branch, add one heap call, capture the gate rejecting it, and revert.
5. Write a short note in `MEMORY.md` naming which section consumed more than you expected and what you changed (or would change) to stay inside the budget.

## Required evidence

- `MEMORY.md` stating numeric byte budgets for `.text`, `.data`, `.bss` and stack
- A captured `size` or linker-map excerpt showing `.data + .bss` at or below the written data budget
- Git history showing the budget written before the store was implemented, not after
- A captured compile, link or CI failure that rejects a deliberate `malloc`/`calloc`/`realloc`/`free` call
- Reflection notes answering the task questions

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit only screenshots of code.

## Acceptance criteria

- [ ] A recursive grep (or equivalent) of the submitted C sources finds no call to `malloc`, `calloc`, `realloc` or `free`.
- [ ] `MEMORY.md` states a number of bytes for each of `.text`, `.data`, `.bss` and stack, plus a total RAM cap of at most 64 KiB for `.data + .bss + stack`.
- [ ] A captured `size(1)` report or linker map shows `.data + .bss` less than or equal to the `.data + .bss` budget written in `MEMORY.md`.
- [ ] A documented gate rejects a commit that calls `malloc`, and a captured log of that rejection is included.

The mentor may request a live explanation, a change to `N`, or a walk through the map file before approval. Passing a compile alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. Which section (`.text`, `.data`, `.bss`, stack) would blow the budget first if `N` doubled, and how do you know?
2. Name one situation on an edge node where a one-time `malloc` at startup is still the wrong tool, even if it never runs again.

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Open the map or `size` output and ask the apprentice to point at the bytes that belong to the telemetry array.
- Ask what happens if a future change adds a 2 KiB lookup table: which budget line moves, and does the gate still catch a heap call?
- Do not approve if `MEMORY.md` was written after the binary already fitted — the budget has to precede the implementation in history.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
