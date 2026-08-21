# Continuous Integration Pipeline (Term 1 Milestone)

**Task ID:** `be1t1-007`
**Estimated effort:** 14 hours
**Module:** Ci Cd

## Why this task exists

This is the Term 1 milestone. Everything built so far — the API, the schema,
the tests, the container — is only actually reliable if it's checked
automatically on every change. This task closes that loop.

## Authoritative resources

- **GitHub Actions Documentation** (reference): https://docs.github.com/actions

## Work to complete

1. Write a CI workflow that runs the linter, the full test suite against a
   real PostgreSQL service container, and builds the Docker image on every
   push.
2. Configure the pipeline to fail visibly when any step fails.
3. Add a branch protection rule (or a clearly documented equivalent, if your
   hosting doesn't support it) that blocks merging while the pipeline is
   red.
4. Deliberately introduce a failing test or lint error on a branch and show
   the pipeline catching it.
5. Fix the deliberate failure and show the pipeline going green on the fix
   commit.

## Required evidence

- The CI workflow file committed to the repository
- Links to, or exported logs of, both the failing run and the passing run
- Git history showing the deliberate break and its fix as separate,
  identifiable commits
- README section describing the pipeline stages and the branch protection
  setup

## Acceptance criteria

- [ ] The pipeline runs lint, the full test suite against a real database
      service, and a container build on every push.
- [ ] A deliberately broken commit is shown failing the pipeline, with the
      failure visible in the run log.
- [ ] The fix commit is shown turning the pipeline green.
- [ ] Merging is blocked, or documented as blocked, while the pipeline is
      red.

## Reflection

Answer these in your own words after doing the work:

1. What did the pipeline catch that you didn't expect it to catch?
2. What would you still trust only a human reviewer to catch, and why?

Also record:

- What took longer than expected?
- What would you configure differently next time?
- What remains unclear?

## Mentor review guide

- Ask to see the actual failing run in the CI system, not just a description
  of it.
- Ask what happens if someone force-pushes past the branch protection, and
  whether that's actually prevented or just discouraged.

Suggested review outcome: **Approve**, **Request revision**, or **Create
follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes. Solution
generation is not the intended path for this task. Material AI assistance
must be disclosed with the provider/model (if known), purpose, and
verification performed.

## Completion gate

This task is complete only once the evidence is submitted and the mentor
approves the demonstrated pipeline — not when a workflow file merely exists
in the repository.
