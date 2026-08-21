# Apply License Obligations and SemVer to a Real Change

**Task ID:** `os1t1-006`
**Estimated effort:** 7 hours
**Module:** License and SemVer

## Why this task exists

Contribution and review without license and version judgment is incomplete
maintainership. This task is not a license trivia quiz. You will write obligations
from the **project you already work on**, and you will assign a SemVer bump to a
**real** pull request or published release — yours from this term, or a recent
upstream tag you can open.

Do not invent a fictional product version. If the project does not use SemVer, say
so, then still apply SemVer 2.0.0 rules to the public API the README or docs treat
as stable, and write the version string the project *does* publish (tag, package
metadata, or `unversioned` plus the commit SHA).

## Authoritative resources

- **The Open Source Initiative — Licenses** (primary): https://opensource.org/licenses
- **Semantic Versioning 2.0.0** (primary): https://semver.org/

Read the project's `LICENSE` and the SemVer specification itself. Record any extra
pages (for example the project's `CHANGELOG` or API docs).

## Work to complete

1. Copy the SPDX identifier from the project LICENSE or host metadata. Open the
   matching OSI page. Write at least four obligation bullets. Each bullet starts
   with `MUST` or `MUST-NOT` and cites a section heading or clause (license text or
   OSI page). Cover, at minimum: distribution of source or binaries, notice
   preservation, and warranty. Add one bullet about combining with a differently
   licensed dependency.
2. Choose one real change: the pull request from `os1t1-003`, or a published release
   tag / changelog entry on the same project. Record the URL.
3. Record the **current** published version string (git tag, package metadata, or
   `unversioned` plus SHA). Name the public API surface you are using (documented
   CLI flags, exported symbols, HTTP routes, or config keys — pick the one the
   project documents).
4. Propose exactly one bump: `major`, `minor`, or `patch`. Quote the SemVer 2.0.0
   sentence that justifies it. State whether that public API surface changed.
5. If the change added a third-party file or dependency, record that dependency's
   license identifier and whether it is compatible with the project's license in
   one sentence. If none was added, write exactly: `no third-party file added`.

## Required evidence

- The project URL, the SPDX identifier, and the OSI license page URL used
- An obligations list of at least four bullets, each tagged `MUST` or `MUST-NOT`,
  each citing a license section heading or an OSI page heading
- A SemVer decision note naming the current published version string, exactly one
  bump type (`major` / `minor` / `patch`), the public API surface that did or did
  not change, and a quoted SemVer 2.0.0 rule
- The pull-request URL or release-tag URL the bump applies to
- A third-party-file line: either the added dependency's license identifier, or the
  exact sentence `no third-party file added`
- Reflection notes answering the questions below
- AI disclosure entry when AI materially influenced the work

## Acceptance criteria

- [ ] The SPDX identifier in the note matches the project's LICENSE file or the
      host's license metadata.
- [ ] The obligations list contains at least four bullets, each starting with `MUST`
      or `MUST-NOT`, each citing a section heading or clause from the license text
      or the OSI page.
- [ ] The SemVer note names the current version string as published on a tag or in
      package metadata, and proposes exactly one of `major`, `minor`, or `patch`.
- [ ] The SemVer note quotes the SemVer 2.0.0 sentence used and names the public API
      surface that did or did not change.
- [ ] If the change added a third-party file or dependency, its license identifier
      is recorded; otherwise the note contains the exact sentence
      `no third-party file added`.

The mentor may name a different public API surface (for example a documented CLI
flag you did not mention) and ask whether your bump type still holds.

## Reflection

Answer these in your own words after doing the work:

1. If this change had been released with the **wrong** bump (the other of minor vs
   patch, or a skipped major), who would notice first and what would break for them?
2. Which `MUST-NOT` bullet would you put in a pull-request template for this
   project, and why that one rather than a `MUST`?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

Open LICENSE and the SemVer spec. Check that citations are headings that exist, not
paraphrases of a blog. Reject a bump justified only by "it feels small." Confirm the
PR or tag URL is real.

If the apprentice has no mentor this term, a peer can apply the same checks.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the
intended path for this task. Do not let an assistant invent SPDX identifiers,
version strings, or SemVer quotations. The apprentice must be able to open the
cited license clause and the quoted SemVer sentence. Material AI assistance must
be recorded in the submission notes with the provider/model (if known), purpose,
and verification performed.

## Completion gate

This task is not complete when you can recite SemVer. It is complete only after the
obligations list, the bump note, and the real PR or tag URL are submitted and
approved against the acceptance criteria.
