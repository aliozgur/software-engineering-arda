# ISR-safe ring buffer with a contract you can test

**Task ID:** `ie1t1-004`
**Estimated effort:** 8 hours
**Module:** Constrained Memory

## Why this task exists

On an edge node, bytes arrive from a UART ISR, a timer, or a simulated plant thread. The main loop is late. Something has to give — and if you did not write down *what* gives, you already shipped a bug. This task is the first time you treat concurrency as a contract (who may push, who may pop) rather than a hope.

Host-side C only. Simulate the ISR with a POSIX signal, a dedicated thread that *only* calls `push`, or a test harness that interleaves calls. A physical board is optional and never required.

## Authoritative resources

- **GNU Linker (ld) Documentation** (reference): https://sourceware.org/binutils/docs/ld/ — keep the no-heap discipline from `ie1t1-001`; the buffer storage is static or caller-provided.

Use official documentation as the primary source. If you use anything else (C11 atomics notes, your compiler's sanitizer docs), record it.

## Work to complete

1. Write `POLICY.md` first: capacity is a compile-time power of two; overflow is either **drop-newest** (refuse the incoming item, count a drop) or **drop-oldest** (overwrite the head, count an overwrite). Define empty and full in terms of head/tail (or count). Commit this before the implementation.
2. Implement a single-producer, single-consumer ring buffer in C. Storage is a static array or a caller-provided buffer. No heap in the ring-buffer translation unit. Reject a non-power-of-two capacity with `_Static_assert` or a build-failing test.
3. Tests (a small C test program or a documented test runner):
   - fill to capacity and show the overflow policy's drop/overwrite count;
   - write `N+3` items into capacity `N`, then read what remains and print the sequence;
   - empty and full edge cases (pop on empty returns the documented empty result).
4. ISR simulation: one context may call `push` only; `main` (or a consumer thread) may call `pop` only. Run with AddressSanitizer and, if available, ThreadSanitizer; capture the command and the result (clean run, or a report you then fix).
5. Incremental history: policy → empty/full → overflow → ISR test, not one commit.

## Required evidence

- Ring-buffer C sources with no heap calls in that translation unit
- `POLICY.md` naming drop-newest or drop-oldest and the exact full/empty conditions
- A captured wrap-around test (`N+3` into `N`) showing the expected sequence
- A captured ISR-style test with the push/pop contract stated
- Git history showing tests added before or with the overflow policy
- Reflection notes answering the task questions

Submit a repository URL plus a commit reference. Do not submit only screenshots of code.

## Acceptance criteria

- [ ] Capacity is a compile-time power of two; a static assert or a test that fails the build rejects a non-power-of-two capacity.
- [ ] After filling to capacity, the documented overflow policy is observed: `POLICY.md` names drop-newest or drop-oldest, and a captured test reports the count of dropped or overwritten items.
- [ ] A wrap-around test writes `N+3` items into a buffer of capacity `N`, then reads the remaining items; the captured sequence matches the policy in `POLICY.md`.
- [ ] The ISR simulation calls `push` only from the simulated interrupt context and `pop` only from main; the test source or a comment block states that contract, and the captured run completes without a data race sanitizer report (or documents that TSan/ASan was run).
- [ ] A recursive grep of the ring-buffer translation unit finds no call to `malloc`, `calloc`, `realloc` or `free`.

The mentor may ask you to switch overflow policy live and predict the new `N+3` sequence. A green test binary without `POLICY.md` is not enough.

## Reflection

Answer these in your own words after doing the work:

1. For a 1 kHz sensor ISR and a main loop that sometimes stalls for 50 ms, which overflow policy loses which information, and which would you pick for a safety trip versus a telemetry trend?
2. Why is a multi-producer ring buffer a different problem, and what did you *not* implement that would be required for it?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to draw head/tail after `N+3` writes without looking at the log.
- Ask whether `push` from two ISRs would still be safe — if they say yes without a lock or a single-producer proof, request revision.
- Do not approve a buffer that uses modulo on a non-power-of-two "for simplicity" after claiming power-of-two in `POLICY.md`.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
