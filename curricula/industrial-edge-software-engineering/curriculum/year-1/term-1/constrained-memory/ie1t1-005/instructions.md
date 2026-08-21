# Fixed-size pool, OOM policy, and refill measurement

**Task ID:** `ie1t1-005`
**Estimated effort:** 6 hours
**Module:** Constrained Memory

## Why this task exists

The ring buffer stored a stream. A pool stores *objects with lifetimes*: protocol contexts, in-flight OTA chunks, sensor samples that outlive one loop. If OOM and double-free are undefined, you do not have a pool — you have a future hard fault. This task closes Term 1 by making those two failures checkable, and by publishing numbers a mentor can compare to a heap.

Host-side C. No board required.

## Authoritative resources

- **GNU Linker (ld) Documentation** (reference): https://sourceware.org/binutils/docs/ld/ — use a map or `size` report if you want to show the pool's `.bss` cost against `ie1t1-001`'s budget habit.

Use official documentation as the primary source. If you use anything else, record it.

## Work to complete

1. Choose compile-time constants `M` (block count, ≥ 8) and `S` (block size in bytes, ≥ 16). Implement `pool_alloc` / `pool_free` over a static array of `M` blocks. No general-purpose heap for the pool storage.
2. Document three results in `POLICY.md` (or a header comment that the tests print): **ok**, **oom**, **double_free**. `pool_alloc` after `M` live blocks returns **oom** and a null/invalid handle. `pool_free` of an already-free (or never-alloc) handle returns **double_free**.
3. Tests, captured as a program output file:
   - allocate `M`, then `M+1` → oom;
   - allocate one, free it twice → double_free on the second call;
   - allocate `M`, free all, allocate `M` again → all succeed (no permanent leak in the free list).
4. Write `MEASURE.md` for one scripted pattern you name (example: allocate all, free every other block, allocate as many as will fit). Report `S`, `M`, total pool bytes (`M * S` plus any metadata you added), and peak live blocks. If you compare to `malloc` for the same pattern, say so; the comparison is optional.
5. Incremental history: API and policy first, then OOM/double-free tests, then the refill test and `MEASURE.md`.

## Required evidence

- Pool C sources and a test program with incremental Git history
- A captured run showing alloc `M+1` returning the documented OOM result
- A captured run showing double-free returning the documented error
- A captured run showing refill of all `M` blocks after a full free
- `MEASURE.md` with `S`, `M`, total pool bytes, and peak live blocks
- Reflection notes answering the task questions

Submit a repository URL plus a commit reference. Do not submit only screenshots of code.

## Acceptance criteria

- [ ] After `M` successful allocations, allocation `M+1` returns the documented OOM code and a null or invalid handle; both the code and the handle are shown in a captured run.
- [ ] Double-free of the same block returns a documented error (not a crash, not a second successful free).
- [ ] Freeing all `M` live blocks allows a following sequence of `M` allocations to succeed; the captured run prints success for that refill.
- [ ] `MEASURE.md` states integers for block size `S`, block count `M`, total pool bytes, and peak live blocks for one named scripted pattern.

The mentor may ask you to change `M` live and predict the new OOM point. A crash on double-free is a fail, even if "it works when used correctly."

## Reflection

Answer these in your own words after doing the work:

1. What can this pool *not* allocate that `malloc` can, and why is that a feature on an edge node?
2. If two different structs need the pool, do you pad to `S`, run two pools, or reject the design — and what number in `MEASURE.md` changes for each choice?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask where the free-list pointer lives (in-band vs side array) and what happens if a caller writes past `S`.
- Ask them to point at the peak-live number and say whether the scripted pattern could have asked for `M+1` live — if yes, the measurement must show OOM, not a silent reuse.
- Do not approve a pool that uses `malloc` to create the blocks "just on the host."

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
