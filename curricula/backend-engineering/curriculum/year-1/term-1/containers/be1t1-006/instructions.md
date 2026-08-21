# Containerizing the Service

**Task ID:** `be1t1-006`
**Estimated effort:** 12 hours
**Module:** Containers

## Why this task exists

A service that only runs on your machine isn't a backend service yet — it's
a demo. The CI pipeline and every deployment step later in this curriculum
assume the containerized shape you build here already exists and already
works from a clean checkout.

## Authoritative resources

- **Docker Get Started** (reference): https://docs.docker.com/get-started/
- **The Twelve-Factor App** (reference): https://12factor.net/

## Work to complete

1. Write a Dockerfile for the service, using a multi-stage build if it
   meaningfully reduces the final image size.
2. Write a docker-compose file that brings up the service and a PostgreSQL
   container together, with the service waiting for the database to be
   ready before it starts serving.
3. Externalize configuration via environment variables rather than
   hardcoded values, following the Twelve-Factor App's config principle.
4. Confirm the containerized service passes the smoke test and test suite
   from earlier tasks, run inside the containers.
5. Document the exact commands to build, run, and tear down the stack from
   a clean checkout.

## Required evidence

- The Dockerfile and docker-compose.yml committed to the repository
- Terminal output of a clean `docker compose up` and a passing test run
  inside the container
- README documenting build/run/teardown commands and the externalized
  configuration variables
- Git history showing the containerization work in incremental commits

## Acceptance criteria

- [ ] `docker compose up` brings up a working service and database from a
      clean checkout with no manual steps beyond documented environment
      variables.
- [ ] No secret or environment-specific value is hardcoded in the Dockerfile
      or source.
- [ ] The test suite passes when run inside the container against the
      containerized database.
- [ ] The image is tagged and its size is reported in the README.

## Reflection

Answer these in your own words after doing the work:

1. What assumption about your local machine broke first when you
   containerized this?
2. Which twelve-factor principle did you violate at first, and how did you
   fix it?

Also record:

- What took longer than expected?
- What would you containerize differently next time?
- What remains unclear?

## Mentor review guide

- Ask the apprentice to tear the stack down completely and bring it back up
  live, from the committed instructions only.
- Check the Dockerfile and compose file for anything hardcoded that should
  be an environment variable.

Suggested review outcome: **Approve**, **Request revision**, or **Create
follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes. Solution
generation is not the intended path for this task. Material AI assistance
must be disclosed with the provider/model (if known), purpose, and
verification performed.

## Completion gate

This task is complete only once the evidence is submitted and the mentor
approves the demonstrated reproducibility — not when the container merely
builds once on your machine.
