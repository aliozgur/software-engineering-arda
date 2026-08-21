# Map a Real Project's Contribution Surface

**Task ID:** `os1t1-001`
**Estimated effort:** 6 hours
**Module:** Contribution Surface

## Why this task exists

Later tasks in this term ask you to triage, contribute, review, and eventually write a
maintainer packet. Those artifacts are only meaningful if they sit on a **real public
project** you have actually read. This task is where you choose that project and prove
you can describe its contribution surface the way a newcomer-turned-collaborator would.

This is apprenticeship work: LEARN BY DOING. GROW THROUGH MENTORSHIP. Reading the
license list is preparation. Completion is a map a mentor can open without taking your
word for it.

Do not invent a toy repository that pretends to have a community. Pick a public project
that already exists.

## Authoritative resources

- **The Open Source Initiative — Licenses** (primary): https://opensource.org/licenses —
  identify the SPDX identifier and read the license family the project actually uses.
- **ACM Code of Ethics** (primary): https://www.acm.org/code-of-ethics — read the
  sections on honesty, respect, and public work before you comment or contribute later.

Use the linked documents as the primary source. If you use anything else, record it in
your notes and prefer primary texts over tutorial aggregation sites.

## Work to complete

1. Choose one public repository you can clone. It must have an OSI-identifiable license,
   a visible issue tracker, and at least one commit on the default branch dated within
   the last 12 months. Prefer a project you already use or intend to use. Record why you
   chose it in two to four sentences.
2. Clone it. Check out the default branch. Record the remote URL, the branch name, and
   `git rev-parse HEAD`.
3. Follow the project's documented build, install, or test path far enough to run one
   command the README or CONTRIBUTING tells a newcomer to run. Capture the command and
   its exit code. If you are blocked (missing hardware, private dependency, unpaid
   service), write the exact blocker and the last command that failed — do not substitute
   a different project silently; say so in the note.
4. Open `LICENSE` (or the host's license metadata). Write the SPDX identifier. Open the
   matching page on the OSI license list and write one paragraph: what a contributor
   must do, and what they must not assume they may do, under that license.
5. Locate `CONTRIBUTING`, `CODE_OF_CONDUCT`, issue templates, and pull-request templates
   — or record each as `not present`. Quote the contribution path a newcomer is told to
   follow (how to propose a change, whether issues are required first, DCO/CLA if any).
6. Read five recent public issues or pull requests. Build a table: URL, type (issue or
   PR), status (`open` / `closed` / `merged`), one-sentence fit judgment for a first
   contribution this term. Mark at least one row as a candidate for `os1t1-002`.

Keep this project for the rest of the term unless it is abandoned or you cannot
lawfully contribute to it. If you switch later, you will redo this map for the new
repository.

## Required evidence

- A committed Markdown note (for example `docs/contribution-surface.md`) that names the
  public repository URL, default branch, and checked-out commit SHA
- The exact clone, build, and/or test commands run, plus the recorded exit code of the
  last command
- An SPDX license identifier copied from that repository and a one-paragraph obligation
  note citing the matching OSI license page
- A table of at least five distinct public issue or pull-request URLs, each with status
  and a one-sentence contribution-fit judgment
- Quoted path-or-absent notes for CONTRIBUTING and CODE_OF_CONDUCT (or the project's
  equivalent files)
- Reflection notes answering the questions below
- AI disclosure entry when AI materially influenced the work

Submit a repository URL plus an immutable commit reference for the note. Do not submit
only screenshots of the upstream project.

## Acceptance criteria

- [ ] The note records a public repository URL, the default branch name, and a
      40-character commit SHA that exists on that branch.
- [ ] The note records the clone command, the build or test command actually run, and
      that command's exit code.
- [ ] The SPDX identifier in the note matches the repository LICENSE file or the host's
      license metadata for that repository.
- [ ] The table lists at least five distinct public issue or pull-request URLs, each
      with a status of open, closed, or merged and a one-sentence contribution-fit
      judgment.
- [ ] The note states whether CONTRIBUTING and CODE_OF_CONDUCT (or named equivalents)
      exist, with a repository file path if they do, or the exact phrase "not present"
      if they do not.

The mentor may ask you to open one table row live and explain, from the thread alone,
why it is or is not a good first contribution.

## Reflection

Answer these in your own words after doing the work:

1. Which single file or page most changed what you would send as a first patch, and
   what sentence in it caused that?
2. Under this license, what is one thing you are **not** free to do with a copy of the
   code, even though the repository is public?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

Open the named commit SHA on the public host and confirm the SPDX identifier and the
five URLs. Ask the apprentice to defend one "poor fit" row — if they cannot point at a
sentence in CONTRIBUTING, the issue body, or the license, the map is still a reading
log.

If the apprentice has no mentor this term, a peer who was not the author of the note
can run the same checks.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the
intended path for this task. Do not let an assistant invent issue URLs, license
identifiers, or build output. The apprentice must be able to open every URL and
reproduce every command in the note. Material AI assistance must be recorded in the
submission notes with the provider/model (if known), purpose, and verification
performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the
evidence is submitted and the mentor — or, if mentorship is not attached, a recorded
peer check against the acceptance criteria — approves the demonstrated competency.
