# Continuous Integration Pipeline for a Small Service

**Task ID:** `pd1t1-001`
**Estimated effort:** 10 hours
**Module:** CI/CD

## Why this task exists

Every later task in this curriculum assumes a working CI pipeline exists and is trusted. Before you automate releases,
infrastructure or observability, you need a pipeline that reliably tells you when the codebase is broken — and one
you have personally watched fail on purpose, so you know what a false-positive green run would look like.

## Authoritative resources

- **GitHub Actions Documentation** (reference): https://docs.github.com/actions
- **GitLab CI/CD Documentation** (reference): https://docs.gitlab.com/ci/

Pick whichever platform hosts your repository. Use the official documentation as your primary source; if you use
other material, record it in your notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Pick or reuse a small service you control that already has at least one automated test suite and a lint or
   static-analysis tool available for its language.
2. Write a CI pipeline (GitHub Actions or GitLab CI) with separate steps for install/build, lint, and test.
3. Commit a change that deliberately breaks a test. Confirm CI turns red for the right reason, then revert it in a
   follow-up commit.
4. Commit a change that deliberately introduces a lint violation. Confirm CI turns red for that specific reason, then
   revert it in a follow-up commit.
5. Add a short README section explaining what each CI stage checks and why you ordered them the way you did.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Submit a repository URL plus a commit/tag reference. Do not submit only screenshots of a green pipeline.

## Acceptance criteria

- [ ] CI runs automatically on every pushed commit and on every pull/merge request.
- [ ] CI fails the build when a unit test fails, demonstrated by a commit that intentionally breaks a test.
- [ ] CI fails the build when the lint/static-analysis step reports an error, demonstrated by a commit that
      intentionally introduces a lint violation.
- [ ] The pipeline configuration file is committed to the repository and runs successfully from a fresh clone.

Each criterion above should be checkable directly from your Git history and CI run logs — a mentor should not have to
take your word for any of them.

## Reflection

Answer these in your own words after doing the work:

1. What should a green CI run actually prove about the code — and what does it explicitly *not* prove?
2. You had to choose an order for lint and test steps. Why that order, and what would change if you reversed it?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to break the pipeline live — pick a way it hasn't already been broken — and explain what they
  expect to fail before running it.
- Do not approve on the strength of a green run alone; the two intentional-failure commits are the real evidence.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes. Solution generation is not allowed for this
task — writing the pipeline yourself is the point. Any material AI assistance must be disclosed with the
provider/model (if known), what it was used for, and how you verified the result.

## Completion gate

This task is complete only once the evidence is submitted and a mentor has approved the demonstrated pipeline —
including watching it fail correctly, not just watching it pass.
