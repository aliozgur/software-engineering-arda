# Priority inversion you can reproduce and then bound

**Task ID:** `ie1t2-003`
**Estimated effort:** 8 hours
**Module:** Time and Isolation

## Why this task exists

You already have a scheduler that can miss a deadline. This task is the miss that looks like a scheduler bug and is actually a lock. Mars Pathfinder is the folklore; your job is a host-side timeline a mentor can read: High blocked, Medium running, Low still in the critical section — then the same arrivals with a named protocol and a smaller bound.

Implement this on the host (extend `ie1t2-001` or a small preemptive/priority table). FreeRTOS mutex chapters are the authority for the protocol names. You do not need to link the FreeRTOS kernel. No board required.

## Authoritative resources

- **Mastering the FreeRTOS Real Time Kernel** (primary): https://www.freertos.org/Documentation/RTOS_book.html — mutexes, priority inheritance, and (if covered) priority ceiling.
- **MIT 6.1810 — Operating System Engineering** (reference): https://pdos.csail.mit.edu/6.1810/ — concurrency and locking lectures, for the idea that a lock plus a scheduler is a new failure mode.

Use official documentation as the primary source. If you use anything else, record it.

## Work to complete

1. Write `INVERSION.md` with the experiment plan: three tasks Low < Medium < High; Low takes a mutex, then High tries to take it, then Medium runs CPU work. State the tick count `N` you expect High to stay blocked in the *broken* case (Medium's work duration is a good `N`).
2. Implement a priority scheduler (can be a discrete-event loop: at each tick, run the highest-priority ready task for one tick). Add a mutex with **no** inheritance or ceiling first.
3. Reproduction: capture a tick log `tick=<n> run=<task> lock=<owner|none> high_state=<ready|blocked|running>`. Show High blocked for ≥ `N` ticks while Medium runs and Low owns the mutex.
4. Fix: implement **priority inheritance** (Low's effective priority rises to High while it holds the mutex High wants) **or** **priority ceiling** (mutex has a ceiling; holder runs at that ceiling). Name the one you implemented.
5. Re-run the same arrival order. High's contiguous blocked time must be ≤ the bound you write (typically Low's remaining critical-section ticks, not Medium's full work).
6. Add one sentence: a situation the *other* protocol would handle differently (for example, multiple mutexes and chained inversion vs a single ceiling).
7. Commit the broken timeline before the fix.

## Required evidence

- `INVERSION.md` naming the protocol and one difference versus the other protocol
- A captured broken timeline with High blocked ≥ `N` ticks while Medium runs and Low holds the lock
- A captured fixed timeline with High's blocking time ≤ the written bound
- Git history with reproduction before the fix
- Reflection notes answering the task questions

Submit a repository URL plus a commit reference. Do not submit only screenshots of code.

## Acceptance criteria

- [ ] The reproduction log shows three named tasks (Low, Medium, High) and a mutex; High is blocked while Medium is running and Low still owns the mutex for at least the `N` ticks stated in `INVERSION.md`.
- [ ] `INVERSION.md` names exactly one protocol used in the fix: priority inheritance or priority ceiling.
- [ ] The post-fix log, using the same arrival order, shows High's contiguous blocked time less than or equal to the bound written in `INVERSION.md`.
- [ ] `INVERSION.md` contains one sentence naming a situation the other protocol would handle differently.

The mentor may ask you to add a second Medium-priority worker and predict whether the bound still holds. A narrative without tick logs is not enough.

## Reflection

Answer these in your own words after doing the work:

1. If Low's critical section is 2 ticks and Medium's work is 200 ticks, what should `N` be in the broken case, and what should the post-fix bound be?
2. Would disabling interrupts around the critical section have avoided inversion here, and what deadline would that steal from?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Walk the broken log line by line until the apprentice points at the first tick Medium runs while High is blocked.
- Ask them to compute the bound from Low's remaining CS length — if the post-fix log is longer than that, the protocol is incomplete.
- Do not approve a "fix" that only raises Low's *base* priority permanently.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
