# Harden the Image and the Pipeline (Term 2 Milestone)

**Task ID:** `be1t2-007`
**Estimated effort:** 14 hours
**Module:** Hardening

## Why this task exists

This is the Term 2 milestone. The service now has auth, a second
store, a queue, signals, and a load baseline. None of that is
trustworthy if the image runs as root, if known-vulnerable packages
ship silently, or if a secret lives in the workflow file. This task
closes those gaps in the same pipeline Term 1 already built.

## Authoritative resources

- **GitHub Actions Documentation** (reference): https://docs.github.com/actions
- **Docker Get Started** (reference): https://docs.docker.com/get-started/
- **OWASP Top 10** (primary): https://owasp.org/www-project-top-ten/

Use Docker docs for `USER`, multi-stage builds, and secrets-as-env.
Use GitHub Actions docs for the scan step. Use OWASP for the
security baseline you write down — especially cryptographic
failures and security misconfiguration.

## Work to complete

1. Change the image so the final stage runs as a non-root user.
   Prove it with `docker compose run` (or `docker run`) printing
   the user, not with a comment in the Dockerfile.
2. Add an image scan to CI (`trivy`, `grype`, or an equivalent
   that produces a machine-readable report). Name the severity
   that fails the build in the README before you wire the step.
3. Keep lint, the test suite against real service containers
   (Postgres, and MongoDB/RabbitMQ if the tests now need them),
   the image build, and the scan on every push.
4. Supply secrets only through the host environment or the CI
   secrets store. Grep the Dockerfile and workflow YAML for
   passwords, tokens, and keys.
5. Deliberately break the gate: revert to root *or* introduce a
   finding the scan will fail on. Show the red run. Fix it on a
   later commit and show the green run.
6. Write a short security baseline: non-root, scan tool and
   threshold, how secrets enter the process, and one OWASP item
   this milestone does *not* yet close.

The break and the fix must be separate commits, the same way
Term 1's CI milestone required a red run you can still open.

## Required evidence

- The Dockerfile showing a non-root `USER` on the final stage,
  and the workflow file that builds, tests, and scans
- Exported logs of a failing scan or a failing root-user check,
  and of the later passing run
- Git history with the deliberate break and the fix as separate,
  identifiable commits
- A README baseline naming the scan tool, the failing severity,
  and how secrets are supplied
- A grep of the Dockerfile and workflow YAML showing no secret
  values

Submit a repository URL plus a commit reference. Do not submit
only a passing-run screenshot.

## Acceptance criteria

- [ ] The final image stage sets `USER` to a non-root uid or
      named user; `docker compose run whoami` (or equivalent) is
      not root.
- [ ] CI fails when the image scan reports a finding at the
      severity named in the README, shown by a failing run log.
- [ ] No password, token, or API key appears in the Dockerfile
      or the workflow YAML.
- [ ] The pipeline still runs lint, tests against real service
      containers, an image build, and the scan on every push.

The mentor may ask you to open the red run and point at the
exact step that failed, then open the Dockerfile line that
prevents root.

## Reflection

Answer these in your own words after doing the work:

1. What can an attacker do if this container still ran as root?
2. Which findings did you accept (if any), and who agreed?
3. What would still ship if someone force-pushed past this
   pipeline?

Also record:

- What took longer than expected?
- What would you add to the baseline next?
- What remains unclear?

## Mentor review guide

- Open the failing run, not a description of it.
- Confirm `USER` is on the *final* stage, not only on a builder
  stage that gets discarded.
- Reject a workflow that inlines a token or that dropped the
  Term 1 test job to make the scan "fit."

Suggested review outcome: **Approve**, **Request revision**, or
**Create follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and
quizzes. Solution generation is not the intended path for this
task. Material AI assistance must be disclosed with the
provider/model (if known), purpose, and verification performed.

## Completion gate

This task is complete only once the evidence is submitted and
the mentor approves the demonstrated gates — not when a scan
step exists and has never been seen red.
