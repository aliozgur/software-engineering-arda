# CI Security Scanning You Can Explain

**Task ID:** `as1t2-004`  
**Estimated effort:** 10 hours  
**Module:** Security pipeline

## Why this task exists

The reference software-engineering path touches supply-chain hygiene and
CI, but not an AppSec triage loop. This task puts a scanner in GitHub
Actions on a repository you own, forces a written decision on three
findings, and requires a red build on a planted issue so the gate is
shown to work.

This is an apprenticeship task, not a reading checkbox. Completion requires
evidence that you can apply and explain the ideas.

## Scope rule

Run scanners only against the repository you own. Do not point a
scanner, fuzzer, or exploit tool at any third-party system. Plants used
to fail the gate must be obviously local and removed before you submit
the default branch.

## Authoritative resources

- **GitHub Actions Documentation** (reference):
  https://docs.github.com/actions
- **OWASP Top 10** (primary): https://owasp.org/www-project-top-ten/

Use GitHub's docs for workflow syntax, secrets, and permissions. Map
findings to OWASP categories in the triage note.

## Work to complete

1. Add a GitHub Actions workflow that runs at least one SAST tool or
   dependency-advisory scan (for example CodeQL, Semgrep, pip-audit,
   npm audit, or OS-provided advisory data) on push or pull request.
   Pin action versions. Do not store registry credentials in the
   workflow file.
2. Run the workflow on your repository. Export or paste the finding
   list with tool name, finding id or rule, file, and severity.
3. Triage at least three findings as `fix-now`, `fix-later`,
   `false-positive`, or `accepted`. If the first run is clean, plant
   two local issues of a class the tool can see, triage those, then
   remove any plant you do not intend to keep as a demonstration.
4. Fix at least one `fix-now` finding. Reference the finding id in the
   commit message.
5. Write at least three sentences justifying one `accepted` or
   `false-positive` finding: what the tool thought, why you disagree or
   accept the risk, and what would change your mind.
6. On a disposable branch, plant one finding of a class named in the
   notes. Show the workflow failing. Remove the plant and show it
   passing.
7. Update the threat-model register with any new residual risk.

## Required evidence

- Committed GitHub Actions workflow that runs a SAST or
  dependency-advisory scan on push or pull request
- A triage note classifying at least 3 findings as fix-now, fix-later,
  false-positive, or accepted, each with the tool's finding id or rule
  name
- A commit that fixes at least 1 fix-now finding and references that
  finding id
- A written justification of at least 3 sentences for 1 accepted or
  false-positive finding
- Workflow logs showing the job fail on a planted finding of a class
  named in the notes, then pass after the plant is removed
- Reflection note answering the task questions

Submit a repository URL plus an immutable commit or tag, and links or
pasted logs for the workflow runs. Do not submit only a screenshot of
a passing status icon.

## Acceptance criteria

- [ ] A GitHub Actions workflow runs at least one SAST or
      dependency-advisory scan on pull request or push.
- [ ] A triage note classifies at least 3 findings as fix-now,
      fix-later, false-positive, or accepted.
- [ ] At least 1 fix-now finding is fixed in a commit that references
      the finding id or rule name.
- [ ] At least 1 accepted or false-positive finding has a written
      justification of at least 3 sentences.
- [ ] The workflow is shown failing on a planted finding of a class
      named in the notes, and passing after the plant is removed.

The mentor may ask you to defend the accepted finding as if it were a
change-review comment. A green scan with no triage note is not enough.

## Reflection

Answer these in your own words after doing the work:

1. Which finding was noise, and what in the rule or the code made it
   fire?
2. What permission set does the workflow use, and why is
   `contents: read` (or tighter) preferable to a default write token
   if you can use it?
3. What would you do if a dependency advisory had no patch yet?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Pick the accepted finding and argue the opposite side; the
  apprentice should hold or revise with evidence.
- Check that action versions are pinned and that no secret is in the
  YAML.
- Do not approve a workflow that is never shown failing.

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
