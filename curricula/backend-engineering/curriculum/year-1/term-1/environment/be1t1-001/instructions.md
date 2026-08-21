# Backend Development Environment and Workflow

**Task ID:** `be1t1-001`
**Estimated effort:** 8 hours
**Module:** Environment

## Why this task exists

Every task after this one assumes a working, reproducible Python project and a
disciplined commit habit. If the environment is shaky, every later task gets
harder for reasons that have nothing to do with backend engineering. Get it
right once, here, rather than rebuilding it under pressure later.

## Authoritative resources

- **Python 3 Tutorial** (reference): https://docs.python.org/3/tutorial/

Use the linked documentation as the primary source. You may use additional
sources, but record them in your notes and prefer primary documentation over
tutorial aggregation sites.

## Work to complete

1. Create a Python project skeleton with a virtual environment and a declared
   dependency file (`requirements.txt` or `pyproject.toml`).
2. Configure a linter/formatter (for example `ruff` and/or `black`) and run it
   either as a pre-commit hook or as a documented manual step.
3. Set up the Git repository (or a fresh branch in the working repository)
   with a `.gitignore` that actually matches what this project generates.
4. Write a small smoke test or script that proves the environment works —
   something that fails loudly if a dependency or configuration is missing.
5. Commit the setup in more than one incremental commit. A single "initial
   commit" that dumps the whole skeleton at once does not show your actual
   process and will be sent back.

## Required evidence

- Git history showing the environment built up over at least three
  incremental commits, not one dump commit
- The dependency file and lint/format configuration committed to the
  repository
- Output of the smoke test/script run from a clean checkout, pasted into the
  evidence note
- README section explaining how to reproduce the environment from scratch

Submit a repository URL plus a commit reference. Do not submit only
screenshots of code.

## Acceptance criteria

- [ ] The project runs from a clean checkout using only the committed setup
      instructions.
- [ ] The linter/formatter runs without configuration errors.
- [ ] At least three incremental commits exist for the environment setup.
- [ ] The README documents the exact commands to install dependencies and run
      the smoke test.

The mentor may ask you to delete your virtual environment and rebuild it live
before approving. Passing your own smoke test once is not proof it is
reproducible.

## Reflection

Answer these in your own words after doing the work:

1. What part of the environment would break if a teammate followed only your
   README, and how would you know?
2. What did you change after first getting the lint configuration to pass?

Also record:

- What took longer than expected?
- What would you set up differently next time?
- What remains unclear?

## Mentor review guide

- Ask the apprentice to delete their virtual environment and rebuild it live
  during review, using only the README.
- Check that the `.gitignore` is specific to this project, not a generic
  copy-paste with unrelated entries.

Suggested review outcome: **Approve**, **Request revision**, or **Create
follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes. Solution
generation is not the intended path for this task. Material AI assistance
must be disclosed with the provider/model (if known), purpose, and
verification performed.

## Completion gate

This task is complete only once the evidence is submitted and the mentor
approves the demonstrated setup — not when the environment merely runs on
your own machine.
