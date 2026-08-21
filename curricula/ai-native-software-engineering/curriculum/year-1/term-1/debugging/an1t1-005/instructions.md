# Debugging an AI-Introduced Bug

**Task ID:** `an1t1-005`  
**Estimated effort:** 8 hours  
**Module:** Debugging

## Why this task exists

AI-generated code that's wrong is often wrong in a way that reads as plausible — a subtly incorrect boundary condition, a misunderstood library call, a race that only shows up under load. Catching that requires the same methodical debugging discipline you'd use on any bug, and asking AI to hand you the fix directly would skip the exact skill this task exists to build.

This is an apprenticeship task, not a content-consumption checkbox. Completion requires evidence of the diagnosis process, not just a diff that happens to fix things.

## Authoritative resources

- **MIT — The Missing Semester of Your CS Education (debugging and tooling)** (primary): https://missing.csail.mit.edu/2026/

Use the debugging and tooling material as the process model (reproduce, isolate, hypothesize, verify). Official documentation for your language or runtime's debugger and test runner is also in scope; record extra sources in your notes.

## Work to complete

1. Find or construct a bug that originated in AI-assisted code — ideally one of your own from an earlier task, or a bug scenario your mentor provides.
2. Reproduce it minimally: a failing test or a short, runnable script that demonstrates the wrong behavior. Commit the reproduction.
3. Before writing the fix, write down your hypothesis for the root cause.
4. Fix the bug yourself. Do not ask an AI assistant to generate the fix directly — you may use AI to explain an error message or discuss a concept, but the diagnosis and the fix must be yours.
5. Write a regression test and confirm it fails on the pre-fix code and passes on the post-fix code.

## Required evidence

- A minimal, committed reproduction of the bug (a failing test or reproducible script)
- A written note stating the root-cause hypothesis before the fix was applied
- A commit containing the fix, separate from the reproduction commit
- A regression test, run and shown passing, that fails on the pre-fix code and passes on the post-fix code
- AI disclosure entry distinguishing any allowed AI use (explain/hint) from the independently performed diagnosis and fix

Submit a repository URL plus commit references for the reproduction, the hypothesis note, and the fix.

## Acceptance criteria

- [ ] A reproduction exists as a committed failing test or script, runnable independently.
- [ ] The root-cause hypothesis note predates the fix commit.
- [ ] The regression test fails when checked out against the pre-fix commit and passes against the post-fix commit.
- [ ] The note distinguishes what AI assistance was used for, if any, from the independently performed diagnosis and fix.

The mentor may ask you to walk through the failure live, or introduce a variant of the same bug, before approving.

## Reflection

Answer these in your own words after doing the work:

1. What made this bug read as plausible when you first saw the AI-generated code?
2. What would you check first the next time you review AI-generated code, because of what this bug taught you?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask what the apprentice's hypothesis was before the fix, and whether it turned out to be right.
- Verify the regression test actually fails against the pre-fix commit — don't take that on faith.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, and quizzes about the surrounding material. Solution generation is not the intended path for this task — the skill being assessed is independent diagnosis, so asking an assistant to generate the fix would skip the work. Any AI use must still be disclosed with the provider/model (if known), purpose, and what was independently verified.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
