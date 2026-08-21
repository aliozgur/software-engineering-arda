# Profile the Hot Path, Don't Guess It

**Task ID:** `pe1t1-002`
**Estimated effort:** 10 hours
**Module:** Profiling

## Why this task exists

`y3t2-004` in the software-engineering path asks you to "profile and improve" in
one pass. Here the improvement is forbidden. You write down what you think is
slow, then you let a profiler contradict or confirm you. The artifact that
matters is the profile file plus the guess you were willing to be wrong about.

This is an apprenticeship task. Reading a blog about flame graphs is preparation,
not completion.

## Authoritative resources

- **MIT 6.006 - Introduction to Algorithms** (primary):
  https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-fall-2011/
  — use the lectures on asymptotic growth and data structures so you can say
  whether the hot frame is doing linear work, log n work, or something worse,
  and put that next to the measured sample share.

Use those lectures as the primary source for the complexity claim. Prefer
language runtime docs for the profiler itself.

## Work to complete

1. Use the service from `pe1t1-001` (or the same class of workload) under the
   harness you already have. Drive enough work that a profiler has samples.
2. **Before** opening a profiler, write and commit a hypothesis: one function
   or module you believe will dominate CPU, and one you believe will dominate
   allocations. One sentence each, no hedging list of five.
3. Capture a **CPU profile** and an **allocation or heap profile** for the same
   workload. Commit the profile files (pprof, JFR, speedscope export, `py-spy`
   SVG plus the raw dump — a screenshot alone is not the profile).
4. Read the profiles. Copy the hottest CPU frame's symbol **as the tool prints
   it**. State its share as a number from the file (percent of samples, or
   self/total time). Do the same for the hottest allocation frame.
5. Write a complexity note: name the growth class of the hot work (for example
   "scan of n keys" vs "heap/tree lookup") using 6.006 vocabulary, and put the
   measured share beside that claim. If your hypothesis was wrong, say so in
   the same note. **Do not ship an optimization in this task.**

## Required evidence

- Pre-profile hypothesis file (commit before profiles)
- CPU profile file
- Allocation or heap profile file
- Diagnosis note with frame names and numeric shares copied from the profiles
- Complexity note (growth class + measured share)
- Reflection notes

## Acceptance criteria

- [ ] The hypothesis file is committed before the first profile file and names
      a specific function or module.
- [ ] CPU and allocation/heap profile files are both present in the repository
      (binary or text export), not screenshots only.
- [ ] The diagnosis note copies the hottest CPU frame's symbol as it appears in
      the profile and states its share as a percentage or time from that file.
- [ ] The complexity note names a growth class for the hot work and places the
      measured share next to it — no optimization is shipped in this task.

The mentor may open the profile and ask you to point at the frame you named.
If the note names a function that is not in the profile, the task is not done.

## Reflection

Answer these in your own words after doing the work:

1. Was your pre-profile guess correct? If not, what evidence in the profile
   made the real hot frame obvious?
2. If the input size grew 10×, which growth class would you expect to dominate
   next, and what number from this run supports that?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Open the profile with the apprentice. Ask them to find the named frame.
- Ask what they would measure next if that frame disappeared (the next
  bottleneck), still without writing the fix.
- Do not approve a diagnosis that only restates the hypothesis.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes (for example, how a given
profiler is invoked). It must not name the hot function for you from a pasted
profile dump as a substitute for reading it. Disclose material AI assistance
with provider/model, purpose, and verification performed.

## Completion gate

Complete only after the profiles and the pre-registered guess are submitted and
the mentor approves the diagnosis. A pull request that "also makes it faster"
belongs in a later task, not this one.
