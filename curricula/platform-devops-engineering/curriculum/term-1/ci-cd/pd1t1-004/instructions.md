# Build and Test the Image in CI

**Task ID:** `pd1t1-004`
**Estimated effort:** 12 hours
**Module:** CI/CD

## Why this task exists

`pd1t1-001` proved the *source* breaks CI when tests or lint fail. That is not the same as proving the *image* you will later deploy is what CI built. If the only green image lives on your laptop, every later deploy is a leap of faith. This task makes the pipeline produce a SHA-tagged image and run at least one test against that image.

This is an apprenticeship task, not a content-consumption checkbox. Reading Actions or GitLab CI docs is only preparation. Completion requires a failing build you caused on purpose and a passing run that names the SHA tag.

## Authoritative resources

- **GitHub Actions Documentation** (reference): https://docs.github.com/actions
- **GitLab CI/CD Documentation** (reference): https://docs.gitlab.com/ci/
- **Docker Get Started** (reference): https://docs.docker.com/get-started/

Pick the same CI platform you used in `pd1t1-001`. You do not need a paid registry: building and testing on the runner (or loading into a local/in-job engine) is enough. If you push to a free registry, record the registry and the tag.

## Work to complete

1. Extend the existing pipeline with a job that builds the Dockerfile from `pd1t1-002`.
2. Tag the built image with the short or full git SHA of the commit being built. Print that tag in the job log.
3. Add a step that runs tests *against that image* — for example start the container and hit a health endpoint, or run the test suite inside the image. Host-only `npm test` / `pytest` without the image does not satisfy this task.
4. Commit a change that deliberately breaks the image build (a bad `COPY`, a missing dependency, a syntax error in the Dockerfile). Confirm CI goes red for that reason. Revert it in a follow-up commit.
5. Add a README section that states which job builds, which job tests the image, and whether anything is pushed.

## Required evidence

- Committed pipeline file showing an image-build job and a test job that uses that image
- CI log of a passing run that prints the image tag containing the git SHA
- CI log of a commit that breaks the Dockerfile, showing the build job fail for that reason, plus the revert commit
- CI log or captured output of the test step running against the built image, not only against host-installed packages
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Submit a repository URL plus a commit/tag reference. Do not submit only a green checkmark screenshot.

## Acceptance criteria

- [ ] The pipeline builds the Dockerfile on every relevant push and pull/merge request.
- [ ] A test step runs against the image that job just built, not only against dependencies installed on the runner host.
- [ ] A commit that breaks the image build is shown failing CI for that reason, then reverted in a follow-up commit.
- [ ] The built image is tagged with the short or full git SHA, and that tag appears in the CI log.

A mentor should be able to open the failing run and the passing run and match both to commits.

## Reflection

Answer these in your own words after doing the work:

1. What can still be wrong with a SHA-tagged image that passed this pipeline?
2. Why tag with the git SHA rather than only `latest`? What would a rollback look like if `latest` were the only tag?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to show the failing Dockerfile commit and say, before opening the log, which job should go red and with what error class.
- Do not approve if tests run only on the runner host and never start or exec into the built image.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes. Solution generation is not allowed for this task — wiring the image job yourself is the point. Any material AI assistance must be disclosed with the provider/model (if known), what it was used for, and how you verified the result.

## Completion gate

This task is complete only once the evidence is submitted and a mentor has approved both the intentional red build and a passing run that names a SHA-tagged image. LEARN BY DOING. GROW THROUGH MENTORSHIP.
