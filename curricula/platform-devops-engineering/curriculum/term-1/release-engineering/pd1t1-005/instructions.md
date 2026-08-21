# Cut a Reproducible Versioned Release

**Task ID:** `pd1t1-005`
**Estimated effort:** 12 hours
**Module:** Release engineering

## Why this task exists

Later you will roll a bad release *back* to a previous version. That only works if a previous version exists as an immutable, named artifact — not as "whatever was on `main` last Tuesday" and not as the `latest` tag. This task is where you create that contract: SemVer tag, changelog, and an artifact a mentor can rebuild from the tag.

This is an apprenticeship task, not a content-consumption checkbox. Reading CI docs is only preparation. Completion requires two changelog versions and a rebuild from the tag.

## Authoritative resources

- **GitHub Actions Documentation** (reference): https://docs.github.com/actions
- **GitLab CI/CD Documentation** (reference): https://docs.gitlab.com/ci/

Use official documentation for any release workflow you add. Record the SemVer spec (`https://semver.org`) in your notes if you consult it — do not treat a blog post as the source of version meaning.

## Work to complete

Continue the same service. You may cut the release from a pipeline job or from documented local commands; either is acceptable if a mentor can reproduce it.

1. Adopt SemVer for this service. Write one paragraph in `RELEASE.md` stating what a MAJOR, MINOR and PATCH bump means *for this* service (API break, new endpoint, bugfix — be concrete).
2. Add `CHANGELOG.md` with dated entries for at least two versions. Each entry must name a user-facing change, not only "updates" or "fixes".
3. Create a git tag that matches the current version (for example `v0.1.0`) and push it if your remote is part of the evidence.
4. Produce a release artifact named with that version: an image tag (`service:0.1.0`) and/or a versioned archive. Rebuild it from a clean checkout of the tagged commit using only the commands in `RELEASE.md`.
5. Commit the changelog and release notes incrementally. The tag should point at the commit that contains them, not at an empty later commit.

## Required evidence

- Git tag matching a documented SemVer version (for example `v0.1.0`) pointing at a specific commit
- `CHANGELOG.md` with dated entries for at least two versions that name user-facing changes, not only "updates"
- Release artifact tagged with that version (image tag or archive name) plus the command output of rebuilding it from the tagged commit
- `RELEASE.md` listing the exact commands a mentor follows to cut and rebuild the release
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Submit a repository URL plus the tag name. Do not submit only a screenshot of a GitHub/GitLab release page.

## Acceptance criteria

- [ ] A git tag exists whose name matches a documented SemVer version and points at the release commit.
- [ ] `CHANGELOG.md` contains dated entries for at least two versions, each naming at least one user-facing change.
- [ ] A release artifact (container image tag or archive) is named with that version and rebuilds from the tagged commit with the same documented command.
- [ ] `RELEASE.md` lists the cut-and-rebuild commands a mentor can follow without asking you a question.

A mentor should be able to check out the tag, run your documented rebuild, and get an artifact with that version in its name.

## Reflection

Answer these in your own words after doing the work:

1. If you had to roll back tomorrow, which identifier would you give the pipeline — the git tag, the image tag, the changelog date, or `latest` — and why the others would be the wrong handle?
2. What would you refuse to call a "release" even if CI is green?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to walk from the tag to the rebuilt artifact without opening `RELEASE.md` first; then compare to the file.
- Do not approve a changelog whose only entries are "initial commit" and "updates", or a release whose only tag is `latest`.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes. Solution generation is not allowed for this task — choosing what a version means and writing the changelog yourself is the point. Any material AI assistance must be disclosed with the provider/model (if known), what it was used for, and how you verified the result.

## Completion gate

This task is complete only once the evidence is submitted and a mentor has approved a tag, a two-version changelog, and a rebuild from that tag. LEARN BY DOING. GROW THROUGH MENTORSHIP.
