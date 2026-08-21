# Secrets That Never Belong in Git

**Task ID:** `as1t1-006`  
**Estimated effort:** 8 hours  
**Module:** Secrets

## Why this task exists

"Do not commit secrets" is easy to write and easy to miss. This task
requires a scan of history, a rotation or false-positive decision on
every hit, environment-based configuration, and a hook or CI job that
fails on a dummy pattern you document. The failing job is the evidence
the control is real.

This is an apprenticeship task, not a reading checkbox. Completion requires
evidence that you can apply and explain the ideas.

## Scope rule

Work only on a repository you own. Never plant a live credential, and
never scan or push secrets to a repository you do not control. Dummy
secrets used to prove the scanner must be obviously fake and documented.

## Authoritative resources

- **GitHub Actions Documentation** (reference):
  https://docs.github.com/actions

Use the linked documentation for workflow or action configuration if
you put the scanner in CI. A local pre-commit hook is also acceptable.

## Work to complete

1. Run a secret scanner against the current tree *and* git history of
   the owned repository (for example gitleaks, detect-secrets, or
   `git log -p` plus a documented pattern list if you cannot install a
   scanner). Record the command, tool version, and timestamp.
2. Classify every finding as rotated, removed, or false positive. If
   you find a real secret — even a leftover lab password — rotate or
   invalidate it and treat the old value as burned. Do not commit a
   new live secret while doing this.
3. Move application secrets to the environment or an untracked local
   file. Commit an example file (`/.env.example` or equivalent) that
   lists names only. Add the real file to `.gitignore`.
4. Change the app so it fails fast at startup when a required secret
   is missing, rather than falling back to a committed default password.
5. Add a CI job (GitHub Actions) or a pre-commit hook that scans for
   secrets. Plant a dummy secret of a pattern you document in the notes
   (for example `DUMMYSECRET_c0ffee`). Show the job or hook failing,
   then remove the dummy and show it passing. Leave the dummy off the
   submitted default branch.
6. Update the threat-model register for secrets and credential leakage.

## Required evidence

- A scan report (command, tool, and timestamp) covering the current
  tree and git history, with every finding marked rotated, removed, or
  false positive
- Committed `.env.example` (or equivalent) listing secret names only,
  plus `.gitignore` excluding the real secrets file
- Application code that reads secrets from the environment or an
  untracked local file, shown in the diff
- CI job or pre-commit hook configuration, plus logs showing it fail
  on a planted dummy secret and pass after the dummy is removed
- Reflection note answering the task questions

Where configuration is produced, submit a repository URL plus an
immutable commit or tag reference. Do not submit only screenshots.

## Acceptance criteria

- [ ] A secret scan of the repository, including git history, is
      recorded; every finding is listed as rotated, removed, or false
      positive.
- [ ] Application secrets are read from the environment or a local
      untracked file; a committed example file lists names only.
- [ ] `.gitignore` excludes the real secrets file.
- [ ] A CI job or pre-commit hook fails when a planted dummy secret of
      a documented pattern is introduced, and passes once that dummy is
      removed.
- [ ] No live credential is committed in any commit on the submitted
      branch.

The mentor may add the documented dummy pattern on a scratch branch
and ask you to run the scanner. A `.gitignore` with no scan of history
is not enough.

## Reflection

Answer these in your own words after doing the work:

1. Why is removing a secret from the latest commit insufficient if it
   still exists in history?
2. What is the difference between rotating a leaked credential and
   deleting the line from the file?
3. Which findings were false positives, and what signature made the
   scanner fire?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Plant the documented dummy on a scratch branch and watch the
  scanner fail.
- Ask what the apprentice would do if the leak had already been
  pushed to a shared remote.
- Do not approve a committed default password "for local convenience."

Suggested review outcome: **Approve**, **Request revision**, or **Create
follow-up challenge**. Prefer questions that force reasoning over requests
for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is
not the intended path for this task. The apprentice must be able to
explain, modify, test and defend every submitted artifact. Material AI
assistance must be recorded in the submission notes with the
provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only
after the evidence is submitted and the mentor approves the demonstrated
competency.
