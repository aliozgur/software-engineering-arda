# Containerize the Service You Already Test in CI

**Task ID:** `pd1t1-002`
**Estimated effort:** 12 hours
**Module:** Containers

## Why this task exists

A green CI run on the host toolchain does not prove the service will start the same way on another machine. Later tasks ship, observe and roll back an image — not a laptop checkout. You need a Dockerfile you have built and run yourself, and a written reason for every layer that ends up in it.

This is an apprenticeship task, not a content-consumption checkbox. Reading the Docker documentation is only preparation. Completion requires evidence that you can build and run the image from a clean checkout.

## Authoritative resources

- **Docker Get Started** (reference): https://docs.docker.com/get-started/

Use the official documentation as the primary source. If you use other material, record it in your notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

Continue the same small service you put under CI in `pd1t1-001`. Do not start a new toy repo unless that service cannot be containerized at all — if you must switch, say why in the note.

1. Write a `Dockerfile` that installs dependencies, copies the application, exposes one port, and sets a documented start command.
2. Add a `.dockerignore` that keeps `.git`, local environment files, secrets, and build artifacts out of the build context.
3. Pin the base image to a digest or an immutable version tag. Record the pin and why you chose that base in a short README section.
4. Build the image locally. Run it *without* bind-mounting your working tree. Send a request to a documented endpoint (health check or main route) and capture the response.
5. Commit incrementally: Dockerfile, ignore file, README section, then any start-command fixes. Do not squash the work into one final commit.

## Required evidence

- Committed Dockerfile and `.dockerignore` from a clean checkout
- Command output of `docker build` showing a successful image with a digest or image ID
- Command output of `docker run` plus a request to a documented endpoint that succeeds without bind-mounting source code
- A short note listing the base-image pin (digest or immutable tag) and which paths `.dockerignore` excludes
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Submit a repository URL plus a commit/tag reference. Do not submit only screenshots of a running container.

## Acceptance criteria

- [ ] `docker build` succeeds from a clean checkout using only committed files.
- [ ] `docker run` serves the service on a documented port without bind-mounting the working tree.
- [ ] `.dockerignore` excludes `.git`, local env files, and secrets; the note lists those exclusions.
- [ ] The `FROM` instruction pins a digest or an immutable version tag, not an unpinned `latest` tag as the only pin.

Each criterion should be checkable from Git history, the Dockerfile, and the captured command output. A mentor should not have to take your word for any of them.

## Reflection

Answer these in your own words after doing the work:

1. What in the image is *not* proven by the CI pipeline from `pd1t1-001`?
2. You pinned a base image. What would go wrong if you had left it on `latest`, and what trade-off did you accept by pinning?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to change the start command live and predict whether the image still serves the documented endpoint before they rebuild.
- Do not approve if the only successful run bind-mounts the working tree, or if `FROM` is an unpinned `latest`.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes. Solution generation is not allowed for this task — writing the Dockerfile yourself is the point. Any material AI assistance must be disclosed with the provider/model (if known), what it was used for, and how you verified the result.

## Completion gate

This task is complete only once the evidence is submitted and a mentor has approved a locally built image that runs without the working tree mounted. LEARN BY DOING. GROW THROUGH MENTORSHIP.
