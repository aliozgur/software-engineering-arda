# Deploy Through the Pipeline, Not From Your Laptop

**Task ID:** `pd1t3-002`
**Estimated effort:** 20 hours
**Module:** Continuous delivery

## Why this task exists

Term 1 built an image in CI. Term 2 applied manifests by hand. If deploy still happens only from your laptop, you do not have a pipeline you can roll back through — you have a ritual. This task makes a job apply the same manifests and fail when the smoke check fails.

This is an apprenticeship task, not a content-consumption checkbox. Reading Actions or GitLab CI docs is only preparation. Completion requires a red smoke and a green deploy whose version matches the run.

## Authoritative resources

- **GitHub Actions Documentation** (reference): https://docs.github.com/actions
- **GitLab CI/CD Documentation** (reference): https://docs.gitlab.com/ci/

Hosted runners cannot see a kind cluster on your laptop. Acceptable arrangements, all free:

- Create kind (or minikube, if the runner supports it) *inside* the job, load the image, apply, smoke, tear down.
- A self-hosted or local runner (`gitlab-runner`, a GitHub self-hosted runner, or `act` documented as the runner you actually used) that can reach your local cluster.

Record which arrangement you used. Do not require a paid cloud Kubernetes service.

## Work to complete

1. Add a pipeline job that deploys the SHA-tagged or release-tagged image using the manifests (or OpenTofu apply) from earlier tasks.
2. After apply, run a smoke check (HTTP to the Service, `kubectl wait` plus curl, or equivalent). The job must fail if the smoke check fails.
3. Commit a change that makes the smoke check fail (broken probe path, bad command, forced 5xx on `/`). Show that job red. Fix or revert it. Show the next run green.
4. On the green run, show that the deployed image tag (or the version label on the workload) equals the git SHA or release tag of that run.
5. Write a short README section: trigger, runner type, what the smoke hits, how a mentor opens the red and green runs.

## Required evidence

- Committed pipeline job that applies deploy manifests and runs a smoke check
- CI/CD log of a passing run whose deployed image tag equals the git SHA or release tag of that run
- CI/CD log of a commit that fails the smoke check, plus the revert or fix commit that goes green
- A note stating the runner type (hosted kind-in-job, self-hosted, or local runner) with a log line that confirms it
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Submit a repository URL plus the two run URLs or log files. Do not submit only `kubectl apply` from your laptop.

## Acceptance criteria

- [ ] A pipeline job — not a laptop-only command — applies the deploy manifests and runs a smoke check.
- [ ] A commit that makes the smoke check fail is shown failing that job, then corrected in a follow-up commit.
- [ ] The image tag (or equivalent version) deployed by the passing run equals the git SHA or release tag of that run.
- [ ] The evidence note states the runner arrangement and a mentor can see that arrangement in the job log.

A mentor should be able to open the red run and see the smoke check, not a missing checkout.

## Reflection

Answer these in your own words after doing the work:

1. What is still not proven by a green smoke check in CI (data, load, a second replica, DNS outside the job)?
2. If you had deployed from your laptop "just this once," what would you be unable to show a mentor next week?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to point at the log line that prints the deployed tag and match it to the commit SHA or release tag.
- Do not approve a job that only builds, or a smoke check that is `echo ok`.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes. Solution generation is not allowed for this task — writing the deploy job yourself is the point. Any material AI assistance must be disclosed with the provider/model (if known), what it was used for, and how you verified the result.

## Completion gate

This task is complete only once the evidence is submitted and a mentor has approved a pipeline-driven deploy with a red smoke and a version-matched green run. LEARN BY DOING. GROW THROUGH MENTORSHIP.
