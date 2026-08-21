# Cooperative scheduler with a deadline-miss log

**Task ID:** `ie1t2-001`
**Estimated effort:** 8 hours
**Module:** Time and Isolation

## Why this task exists

Term 1 stored bytes. Term 2 spends time. A plant loop that "usually keeps up" is not a real-time design — a schedule you can overload on purpose is. You will build a cooperative scheduler on the host so a mentor can run both the feasible set and the miss without a board or an RTOS port.

FreeRTOS is the conceptual reference, not a required runtime. Do not buy a kit. QEMU is optional.

## Authoritative resources

- **Mastering the FreeRTOS Real Time Kernel** (primary): https://www.freertos.org/Documentation/RTOS_book.html — read the chapters on tasks, the idle task, and tick. You are implementing a *cooperative* slice, not the full FreeRTOS preemptive kernel.

Use the official book as the primary source. If you use anything else, record it.

## Work to complete

1. Write `SCHED.md` first: policy is **cooperative** (a scheduled function runs until it returns); ordering is **fixed table order** or **rate-monotonic** (you pick one and name it); tick source is an incrementing integer driven by the host (sleep, `clock_gettime`, or a unit-test increment).
2. Implement a scheduler in C that registers at least three tasks. Each task has: `id`, `period_ticks`, and a `run` function whose compute cost the driver can set (a busy loop of `cost_ticks` or a callback argument).
3. Each tick: decide which tasks are due, run them according to the policy, and if a task's completion tick is past `last_release + period`, increment that task's miss counter and log `miss task=<id> tick=<n>`.
4. Feasible experiment: choose periods and costs that you claim are schedulable. Run ≥ 1000 ticks. Capture a log that prints total misses = 0.
5. Overload experiment: raise **one** task's cost so `cost_ticks >= period_ticks` (or otherwise make it unschedulable under your policy). Run the same horizon. Capture a log that attributes at least one miss to that task id.
6. Commit the feasible run and `SCHED.md` before the overload change.

## Required evidence

- `SCHED.md` naming the policy and the tick source
- Scheduler C sources and a three-task driver
- A captured feasible run (≥ 1000 ticks, 0 misses)
- A captured overload run with at least one miss attributed to a task id
- Git history showing the feasible run before the overload experiment
- Reflection notes answering the task questions

Submit a repository URL plus a commit reference. Do not submit only screenshots of code.

## Acceptance criteria

- [ ] Three tasks are registered with a period in ticks and a recorded compute cost.
- [ ] A captured run with a feasible set prints a miss count of 0 over at least 1000 ticks.
- [ ] A captured run with one task's cost raised so that `cost_ticks >= period_ticks` prints at least one deadline miss whose log line names that task's id.
- [ ] `SCHED.md` states in one paragraph that the scheduler is cooperative and names the tick source.

The mentor may ask you to add a fourth task live and say whether the feasible set remains feasible. A scheduler that never logs a miss is incomplete.

## Reflection

Answer these in your own words after doing the work:

1. Under your chosen ordering, which of the three tasks misses first when you scale *all* costs by 1.5×, and why that one?
2. What can a cooperative scheduler *not* preempt, and what plant symptom would that cause if a `run` function blocked on I/O?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to compute a rough utilization (sum of cost/period) for the feasible set and say whether it is below or above 1.
- Ask what would change if the scheduler were preemptive — they should name a race with `ie1t1-004`'s ring buffer.
- Do not approve a miss log that only prints a global counter with no task id.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
