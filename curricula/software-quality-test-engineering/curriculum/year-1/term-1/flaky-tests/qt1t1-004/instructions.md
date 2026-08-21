# Diagnose and Remediate a Flaky Test Suite

**Task ID:** `qt1t1-004`  
**Estimated effort:** 16 hours  
**Module:** Flaky tests

## Why this task exists

A team that routinely reruns failing CI jobs stops trusting red pipelines, which
erases the value of automated testing entirely. A flaky test is a reliability
defect, not a nuisance to route around.

This is an apprenticeship task, not a content-consumption checkbox. Adding a
retry and calling it done is a failed submission.

## Authoritative resources

- **GitHub Actions Documentation** (reference): https://docs.github.com/actions
- **GitLab CI/CD Documentation** (reference): https://docs.gitlab.com/ci/

Pick whichever platform hosts your repository. Use the official documentation as
your primary source; if you use other material, record it in your notes and
prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Start from a suite that fails intermittently. If you do not already have one,
   introduce a realistic source of nondeterminism (shared mutable state, clock
   or timezone dependence, unordered collections treated as ordered, a race)
   and then diagnose from the failing runs as if you did not plant it. A
   `Math.random()` assertion written only to fail on purpose is not a flake.
2. Reproduce the failure at a measured, nonzero rate. State the run count and
   the number of failures (local loop or CI history). Capture the output.
3. Isolate the actual mechanism. Name it in the fixing commit message — shared
   fixture, leaked time, sort-order assumption — not "fixed flaky test."
4. Fix the underlying nondeterminism. Do not paper over it with a retry, a
   longer sleep, or `retry: 3` in CI as the primary fix. A retry may exist as a
   temporary safety net only if the commit also removes the root cause.
5. Re-run the same repeated-run check at a comparable or higher run count and
   show zero failures.
6. Commit a CI configuration change related to this class of failure: fail on
   flake detection, quarantine with a ticket link, or a job that reruns the
   offending file N times on every push. The change must be about catching or
   handling flakes, not just "also run tests."

## Required evidence

- CI run history or repeated local run output showing the failure rate before
  the fix
- A commit isolating and fixing the root cause, with a commit message naming
  the actual mechanism
- CI run history or repeated run output after the fix showing zero failures
  across a comparable number of runs
- The CI configuration diff related to this fix
- A reflection note answering the task's questions

Submit a repository URL plus a commit or tag reference. Do not submit only a
screenshot of a later green run.

## Acceptance criteria

- [ ] The failure is reproduced at a measured, nonzero rate before the fix, with
      the run count stated.
- [ ] The fixing commit names the specific nondeterminism mechanism, not just
      "fixed flaky test."
- [ ] The same repeated-run check shows zero failures after the fix, at a
      comparable or higher run count.
- [ ] A CI configuration change related to catching or handling this class of
      failure is committed.

The mentor may ask you to reintroduce the old nondeterminism and predict the
failure rate before running it. A single green CI job is not proof.

## Reflection

Answer these in your own words after doing the work:

1. What made this look like "the test is bad" instead of "the code is racy,"
   and how did you tell the two apart?
2. Why is a retry the wrong primary fix for the mechanism you found?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to explain the mechanism without opening the fixing
  commit, then confirm the message names that same mechanism.
- Do not approve a submission whose only CI change is `retry: 3`.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the
intended path for this task. The apprentice must be able to explain, modify, test
and defend every submitted artifact. Material AI assistance must be recorded in the
submission notes with the provider/model (if known), purpose, and verification
performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the
evidence is submitted and the mentor approves the demonstrated competency.
