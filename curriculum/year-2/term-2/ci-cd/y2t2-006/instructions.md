# Continuous Integration and Release Discipline

**Task ID:** `y2t2-006`  
**Estimated effort:** 14 hours  
**Module:** Ci Cd

## Why this task exists

Make quality checks repeatable and releases intentional.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **GitHub Actions Documentation** (reference): https://docs.github.com/actions
- **GitLab CI/CD Documentation** (reference): https://docs.gitlab.com/ci/
- **Semantic Versioning 2.0.0** (reference): https://semver.org/

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Create CI for build, tests, lint/static analysis and artifact creation using GitHub Actions or GitLab CI.
2. Add branch protection expectations to documentation.
3. Define semantic versioning policy and changelog format.
4. Tag and publish a release artifact.
5. Make CI fail intentionally, diagnose it and record the lesson.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] CI is green from a clean checkout.
- [ ] A failing test blocks release.
- [ ] Versioning policy has examples for patch/minor/major.
- [ ] Release notes describe user-visible change and known limitations.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. What should CI prove before merge?
2. What is the difference between continuous integration and continuous deployment?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Review pipeline for unnecessary complexity and secret exposure.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that
force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, quizzes and review unless the mentor further restricts it. Solution generation
is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must
be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the
mentor approves the demonstrated competency.
