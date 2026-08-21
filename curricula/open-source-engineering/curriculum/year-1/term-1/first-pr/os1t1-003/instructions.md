# Open a Justified Contribution

**Task ID:** `os1t1-003`
**Estimated effort:** 10 hours
**Module:** First PR

## Why this task exists

A contribution that never leaves your machine is private practice. This term measures
whether you can put a **small, justified change** in front of another person, linked to
a real public issue, using Git the way that project uses it.

Preferred evidence is an upstream pull-request URL. If you cannot open an upstream PR
this week (CLA you will not sign yet, maintainers asked for discussion first, the
window is too short, your employer forbids posting), the fallback is still a real
project: clone the public repository, keep the upstream remote, open a pull request
**on your public fork**, and keep the upstream issue URL in the description. That is
not a simulated community. Do not create a toy repo with fake issues and pretend it is
open source.

## Authoritative resources

- **Pro Git** (reference): https://git-scm.com/book/en/v2 — read *Distributed Git* and
  the hosting chapter that matches your host (for example *GitHub*) before you fork,
  branch, or open the pull request. Use it again if you rebase onto the current
  default branch.

Use the project's CONTRIBUTING as the other primary source. Record any extra pages.

## Work to complete

1. Start from the issue you triaged in `os1t1-002`, or from another **existing** public
   issue on the same project. The issue URL must appear in the first twenty lines of
   the pull-request description. Do not invent an issue to justify a change you already
   wanted to make.
2. Fork or clone. Add or verify remotes: `origin` (your fork or clone) and `upstream`
   (the public project). Record `git remote -v`.
3. Branch from current default-branch HEAD. Make the smallest change that addresses
   the issue: documentation, test, or a tightly scoped code fix. Follow the project's
   commit-message and test rules. Produce **at least two commits** (for example:
   failing or documenting reproduction, then the fix). Do not squash into one dump
   commit before submission unless CONTRIBUTING requires a single commit — if it does,
   keep the two-commit history on a side branch and record that requirement.
4. Rebase or merge as the project asks so the branch is based on current default
   branch. Do not force-push to a branch other people already pulled unless the
   project requires it; this week you are usually the only pusher on the branch.
5. Open the pull request **upstream** if you can. If you cannot, open it on your
   **public fork** against a branch that exists on that fork, and write in the
   description: upstream clone URL, upstream issue URL, and the reason you did not
   open upstream this week.
6. In the description, write at least three sentences on the user-visible or
   maintainer-visible effect, and list every top-level path the diff touches.
7. Quote, in a short convention note, the commit, test, or DCO/CLA rule you followed,
   with the file path. If a CLA or DCO blocked an upstream PR, that is a valid reason
   to use the fork fallback — write the blocker, do not skip the PR.

## Required evidence

- The public upstream issue URL the change addresses
- Either the upstream pull-request URL, or the fork pull-request URL plus the fork
  clone URL and the upstream clone URL
- Git log of the contribution branch showing at least two commits, with SHAs
- The pull-request description text, including a list of every top-level path the
  diff touches
- A short convention note quoting the project's commit, test, or DCO/CLA rule and the
  file path it came from
- Reflection notes answering the questions below
- AI disclosure entry when AI materially influenced the work

Submit the PR URL (upstream or fork) plus the commit SHAs. Do not submit only
screenshots of a diff.

## Acceptance criteria

- [ ] The pull-request description names the upstream issue URL in the first twenty
      lines.
- [ ] The contribution branch contains at least two commits, shown by `git log` SHAs
      in the evidence note.
- [ ] The pull-request description lists every top-level path the diff touches, and
      the opened diff contains no other top-level path.
- [ ] The description contains at least three sentences on the user-visible or
      maintainer-visible effect.
- [ ] Either the pull-request URL is on the upstream public repository, or the note
      includes the fork pull-request URL, the upstream clone URL, and the upstream
      issue URL, and states that the fork was cloned from that public repository.

The mentor may ask you to walk `git log --oneline --decorate` and `git remote -v` live
and explain which commit first made the issue's failure visible.

## Reflection

Answer these in your own words after doing the work:

1. Which file did you almost include and then leave out, and what made it out of
   scope for this issue?
2. If a maintainer asked you to split this pull request, where would you cut it, and
   which commit SHA would stay in the first half?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

Open the PR URL. Confirm the issue URL, the path list, and two commits. Do not approve
a single-commit dump, a PR with no issue URL, or a private branch that never became a
PR on a public fork or upstream. The fork fallback is valid only when the fork is of
the named public repository.

If the apprentice has no mentor this term, a peer who did not author the PR can apply
the same checks.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the
intended path for this task. Do not let an assistant write the pull-request
description or the patch you submit under your name. The apprentice must be able to
explain, modify, and defend every hunk. Material AI assistance must be recorded in
the submission notes with the provider/model (if known), purpose, and verification
performed.

## Completion gate

This task is not complete when the tests pass locally. It is complete only after the
public (upstream or fork) pull-request URL, the issue URL, and the two-commit history
are submitted and approved against the acceptance criteria.
