# Run the Service and a Dependency with Compose

**Task ID:** `pd1t1-003`
**Estimated effort:** 12 hours
**Module:** Compose

## Why this task exists

A single container is not how this service will run in later terms. You need a local stack — application plus at least one real dependency — that another person can start from a clean checkout. Healthchecks and a named volume are the difference between "it came up on my machine" and a runtime you can later observe and replace.

This is an apprenticeship task, not a content-consumption checkbox. Reading Compose documentation is only preparation. Completion requires a stack a mentor can start and a persistence demo they can replay.

## Authoritative resources

- **Docker Get Started** (reference): https://docs.docker.com/get-started/

Use the official Compose sections of the Docker documentation as the primary source. If you use other material, record it in your notes.

## Work to complete

Reuse the image from `pd1t1-002` and the same service. Add one dependency the service actually talks to (PostgreSQL, Redis, or an equivalent you already use — not a second copy of the app).

1. Write a Compose file that starts the application and the dependency on one user-defined network.
2. Give both services a healthcheck. Make the application start (or become ready) only after the dependency is healthy.
3. Put dependency data on a *named* volume, not an anonymous one and not a host bind-mount of a data directory unless you document why a bind-mount is required.
4. Bring the stack up from a clean checkout. Send a smoke request to the application that causes a write to the dependency (create a row, set a key, or the equivalent).
5. Remove the dependency container (`compose rm -f` / `docker rm` of that service) and start it again. Show that the written data is still there. Capture both the smoke request and the post-restart check.

## Required evidence

- Committed Compose file declaring the app and at least one dependency, plus healthcheck blocks
- Command output of `compose up` showing both services healthy
- A captured smoke request against the running stack that succeeds using the published port
- Command output showing the dependency restarted and previously written data still present on a named volume
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Submit a repository URL plus a commit/tag reference. Do not submit only a screenshot of `compose ps`.

## Acceptance criteria

- [ ] `compose up` from a clean checkout starts the application and at least one dependency.
- [ ] Both the application and the dependency define a healthcheck; compose reports both healthy.
- [ ] Services reach each other by Compose service name, not by a host-only IP address.
- [ ] After the dependency container is removed and started again, data written during the demo is still present on a named volume.

A mentor should be able to replay the persistence demo from your README commands.

## Reflection

Answer these in your own words after doing the work:

1. What does a healthy Compose stack prove about production readiness — and what does it explicitly *not* prove?
2. Why did you choose a named volume over a bind-mount for the dependency data, or why was a bind-mount the better choice here?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to point at the hostname the application uses to reach the dependency, then ask what happens if that name is replaced with `localhost`.
- Do not approve a stack whose only persistence is an anonymous volume, or whose application has no healthcheck.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes. Solution generation is not allowed for this task — writing the Compose file yourself is the point. Any material AI assistance must be disclosed with the provider/model (if known), what it was used for, and how you verified the result.

## Completion gate

This task is complete only once the evidence is submitted and a mentor has approved a stack that stays healthy and keeps its data across a dependency restart. LEARN BY DOING. GROW THROUGH MENTORSHIP.
