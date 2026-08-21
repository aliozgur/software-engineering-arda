# Security Review and a Repeatable Release

**Task ID:** `be1s-004`
**Estimated effort:** 18 hours
**Module:** Release

## Why this task exists

You can operate the stack. You still need a release you can
point at and a rollback you have actually rehearsed. This task
also forces a security review of the *running* service — not a
checklist copied from OWASP with every box ticked in one
sitting.

## Authoritative resources

- **GitHub Actions Documentation** (reference): https://docs.github.com/actions
- **OWASP Top 10** (primary): https://owasp.org/www-project-top-ten/
- **Docker Get Started** (reference): https://docs.docker.com/get-started/

Use Actions for tag workflows and image publish. Use OWASP as
the review prompt, not as a scorecard to complete in the
abstract.

## Work to complete

1. Add or extend a release pipeline that, on a version tag,
   runs the test suite, scans the image at the Term 2
   threshold, and publishes the image. The published image
   tag must be the same string as the git tag.
2. Cut two tags: a "previous" tag (can be the first passing
   build) and a "current" tag. You need both for the rollback
   dry-run.
3. Against the running current release, execute a security
   review that at least covers: authentication and
   authorization on a protected route, one injection attempt
   on an input the API accepts, and a secrets check (env,
   logs, image history). Write findings as you go.
4. Fix at least one finding, or record an accepted risk that
   names the mentor. A review with zero findings and no
   accepted risk will be sent back — look harder.
5. Write rollback instructions that name the previous image
   tag and the exact compose or deploy commands. Dry-run
   them (switch the running stack to the previous tag, then
   back). Keep the transcript.
6. Confirm the tagged release still emits request ids and
   the SLO signals from `be1s-003`. A release that drops
   instrumentation is not a release.

Commit the review notes before the fix. The review is process
evidence; a single "release + review" dump is not.

## Required evidence

- A git tag whose name matches the published image tag, plus
  the pipeline log for that tag showing tests, scan and
  publish
- A security-review note covering authn/authz, injection,
  and secrets, with at least one finding
- The commit that fixes the finding, or a written
  accepted-risk with the mentor named in the evidence note
- Rollback instructions that name the previous image tag
  and the exact commands, plus a dry-run transcript
- Git history showing review notes before the fix commit,
  and a scrape or log from the tagged release proving
  request ids still work

Submit a repository URL plus a commit reference. Do not
submit only a registry screenshot.

## Acceptance criteria

- [ ] A git tag exists and the published image tag string is
      identical to that git tag.
- [ ] The pipeline log for that tag shows tests, the image
      scan, and an image publish step.
- [ ] The security-review note contains at least one finding
      and either a fix commit or an accepted-risk line that
      names the mentor.
- [ ] Rollback instructions name the previous image tag and
      the exact commands; a dry-run transcript shows those
      commands executed.

The mentor may ask you to roll back live and then identify
the current tag from the running container, not from memory.

## Reflection

Answer these in your own words after doing the work:

1. Which finding was real, and how did you confirm it was
   not a false positive?
2. What would you lose if you rolled back right now, besides
   the latest feature?
3. Which observability signal would tell you the rollback
   landed?

Also record:

- What took longer than expected?
- What would you automate next in the release path?
- What remains unclear?

## Mentor review guide

- Compare the git tag string to the image tag string
  character for character.
- Pick one review finding and ask for the request that
  demonstrated it.
- Reject a zero-finding review and a rollback procedure
  that says "redeploy the old version" without a tag.

Suggested review outcome: **Approve**, **Request revision**,
or **Create follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and
quizzes. Solution generation is not the intended path for
this task. Material AI assistance must be disclosed with
the provider/model (if known), purpose, and verification
performed.

## Completion gate

This task is complete only once the evidence is submitted
and the mentor approves the demonstrated release — not
when a tag exists on a branch that never published.
