# Verify the Fix: Security Regression Suite

**Task ID:** `as1t2-002`  
**Estimated effort:** 12 hours  
**Module:** Verification

## Why this task exists

Earlier tasks each proved one class of fix. This task gathers those
proofs into a suite a mentor can run with one command, tied back to the
threat-model register. Reverting a fix and watching the matching test
fail is required — that is how you show the test observes the defect,
not just that the happy path is green.

This is an apprenticeship task, not a reading checkbox. Completion requires
evidence that you can apply and explain the ideas.

## Scope rule

Run tests only against the application you own or the local lab you
operate. Do not point the suite at any third-party host.

## Authoritative resources

- **OWASP Top 10** (primary): https://owasp.org/www-project-top-ten/

Map each test to a Top 10 category or to a threat id from `as1t1-001`.

## Work to complete

1. Inventory the controls already in the app from term 1 and
   `as1t2-001`: authentication, authorization, injection, XSS, CSRF,
   and secrets not appearing in responses.
2. Write or gather at least eight automated tests covering at least
   four of those classes. Name each test after a threat-model id or an
   OWASP category (for example `test_authz_T03_idor` or
   `test_a03_injection_search`).
3. Document one command that runs the full suite (for example
   `make test-security` or `npm test -- security`).
4. On a disposable branch, revert at least two earlier fixes one at a
   time. Run the matching tests. Record the failing output. Restore the
   fixes and record the passing output. Do not merge the reverted
   state.
5. Build a test-inventory table: test name, class, threat id or OWASP
   category, command.
6. Update the threat-model register so every mitigated threat that now
   has a regression test says so.

## Required evidence

- A test-inventory table listing each test, the threat-model id or
  OWASP category it guards, and the command that runs the suite
- Git history showing the suite grown across multiple commits, not
  added in one dump
- Command output of the full suite passing, with a timestamp
- Command output of at least 2 named tests failing after their fix is
  reverted, then passing after restore
- Reflection note answering the task questions

Where code is produced, submit a repository URL plus an immutable commit
or tag reference. Do not submit only screenshots of test output without
the command.

## Acceptance criteria

- [ ] The suite contains at least 8 tests covering at least 4 of:
      authentication, authorization, injection, XSS, CSRF,
      secrets-not-in-response.
- [ ] Each test file or test name references a threat-model threat id
      or an OWASP category.
- [ ] At least 2 tests are shown failing when their corresponding fix
      is reverted, then passing when the fix is restored; commands and
      outputs are recorded.
- [ ] The full suite runs to completion with a single documented
      command.

The mentor may revert a third fix live and ask which test should fail.
A green suite with no revert demonstration is not enough.

## Reflection

Answer these in your own words after doing the work:

1. Which test looked green for the wrong reason until you reverted the
   fix, and what was it actually asserting?
2. Which threat in the register still has no test, and why did you
   leave it untested this term?
3. What would make this suite flaky, and how did you avoid that?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Revert one named fix on a scratch branch and ask the apprentice to
  predict the failing test before running it.
- Check that test names map to the register, not to generic
  `test_login_works`.
- Do not approve a single-commit dump of tests with no revert
  evidence.

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
