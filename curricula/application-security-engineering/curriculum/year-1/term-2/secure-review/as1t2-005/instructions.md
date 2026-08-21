# Secure Code Review with a Written Verdict

**Task ID:** `as1t2-005`  
**Estimated effort:** 8 hours  
**Module:** Secure review

## Why this task exists

Most professional AppSec time is spent on diffs, not on building a
vulnerable lab. This task asks you to review application code you own
— an earlier pull request, a prepared branch, or a teammate's change
you are allowed to read — and produce a verdict a mentor can act on:
severity, mapping, hunk, fix, and scope.

This is an apprenticeship task, not a reading checkbox. Completion requires
evidence that you can apply and explain the ideas.

## Scope rule

Review only code you own or have permission to review. Do not scan,
copy, or "test" a third-party product. PortSwigger Academy is reading
for weakness classes only — do not run hosted labs as a substitute for
reviewing your diff.

## Authoritative resources

- **OWASP Top 10** (primary): https://owasp.org/www-project-top-ten/
- **PortSwigger Web Security Academy** (reading only):
  https://portswigger.net/web-security

Use the articles to name weakness classes (access control, injection,
XSS, CSRF). Apply those names to hunks in your diff, not to a hosted
target.

## Work to complete

1. Choose a diff of at least 40 lines of application code (handlers,
   queries, templates, auth). Documentation-only diffs do not count.
   If your recent history is too small, create a feature branch that
   changes real behaviour, then review that branch.
2. Read the diff as a reviewer. Look for the classes this path already
   taught: authentication, authorization, injection, encoding, CSRF,
   secrets, headers, CORS. Also note anything those classes do not
   cover and mark it `outside Top 10` if needed.
3. Write at least four findings. Each finding must include: severity
   (`high`, `medium`, or `low`), OWASP category or CWE id, file and
   hunk (or line range), and a recommended fix. If the diff is already
   clean, you may seed issues on a review-source branch, review that
   branch, then fix — say so in the notes.
4. Mark at least one finding `must-fix` and at least one
   `non-blocking`. Apply must-fix items, or add residual-risk rows
   for any you leave open.
5. Write an out-of-scope paragraph (for example: dependency CVEs,
   infrastructure IAM, denial of service, or third-party widgets you
   did not open).
6. Update the threat-model register with new findings.

## Required evidence

- The reviewed diff (pull request link or committed patch) of at
  least 40 lines of application code, not only documentation
- A written review with at least 4 findings, each listing severity
  (high, medium, or low), OWASP category or CWE id, file and hunk,
  and a recommended fix
- At least 1 finding marked must-fix and at least 1 marked
  non-blocking
- Commits applying must-fix items, or residual-risk entries for any
  must-fix item left open
- An out-of-scope paragraph stating what this review did not cover
- Reflection note answering the task questions

Submit a repository URL plus an immutable commit or tag. Do not submit
only a bullet list of OWASP names with no hunks.

## Acceptance criteria

- [ ] The review covers a diff of at least 40 lines of application
      code (not only documentation).
- [ ] The review lists at least 4 findings, each with severity (high,
      medium, or low), OWASP category or CWE id, file and hunk, and a
      recommended fix.
- [ ] At least 1 finding is marked must-fix and at least 1 is marked
      non-blocking.
- [ ] Must-fix items are applied in follow-up commits, or each leftover
      must-fix has a residual-risk entry in the threat-model register.
- [ ] The review states what was out of scope so it is not a generic
      checklist.

The mentor may pick one finding and ask you to show the hunk and the
fix without looking at the write-up. A review that only restates
"validate all input" is not enough.

## Reflection

Answer these in your own words after doing the work:

1. Which finding was the easiest to over-severity, and what made you
   keep or lower it?
2. What did you mark out of scope, and what would a follow-up review
   need in order to cover it?
3. How is a secure-review finding different from a scanner finding
   with the same OWASP label?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to open one hunk and explain the finding without
  reading the write-up aloud.
- Challenge the must-fix versus non-blocking split.
- Do not approve a four-item checklist that never cites a file.

Suggested review outcome: **Approve**, **Request revision**, or **Create
follow-up challenge**. Prefer questions that force reasoning over requests
for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is
not the intended path for this task. If AI drafted review comments, the
apprentice must still be able to walk each hunk. Material AI assistance
must be recorded in the submission notes with the provider/model (if
known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only
after the evidence is submitted and the mentor approves the demonstrated
competency.
