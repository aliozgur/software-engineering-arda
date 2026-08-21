# Harden, Verify and Record Residual Risk

**Task ID:** `as1t2-006`  
**Estimated effort:** 14 hours  
**Module:** Capstone

## Why this task exists

The rest of this path produced pieces: a model, class-by-class fixes,
a regression suite, headers, a scanner, a review. This task is the
join. You update the register so nothing is silently `open`, keep the
suite and the CI scan green on one commit, and write an evidence pack
a mentor can walk without hunting through history.

This is an apprenticeship task, not a reading checkbox. Completion requires
evidence that you can apply and explain the ideas.

## Scope rule

Work only on the application you own or the local lab you have operated
throughout this path. Do not "validate" anything against a third-party
host. LEARN BY DOING. GROW THROUGH MENTORSHIP. — the pack is how both
happen in public on your own work.

## Authoritative resources

- **OWASP Top 10** (primary): https://owasp.org/www-project-top-ten/
- **GitHub Actions Documentation** (reference):
  https://docs.github.com/actions
- **HTTP Semantics — RFC 9110** (deep_dive):
  https://www.rfc-editor.org/rfc/rfc9110

Use these to justify residual-risk language (which category remains,
which HTTP behaviour you accepted, which pipeline gate still exists).

## Work to complete

1. Re-read the `as1t1-001` register and every later update. Give every
   original threat a status of `mitigated`, `accepted`, or
   `transferred`. If anything is still `open`, add a next action and
   a named owner (you, or "out of scope for this path").
2. Close remaining `fix-now` items you are willing to finish in this
   task. Put each in its own commit. Do not silently drop them.
3. Run the `as1t2-002` suite on the commit you will submit. Record the
   command, date, and full output.
4. Confirm the `as1t2-004` workflow is green on that same commit.
   Record the run id or paste the log.
5. Confirm the secret scan from `as1t1-006` still passes on that
   commit, and that the header capture from `as1t2-003` still matches
   the notes (re-capture if the app changed).
6. Write `docs/evidence-pack.md` (or equivalent) with links or
   relative paths to: threat model, classification table, regression
   output, CI run, secret-scan result, header capture.
7. Write at least two accepted residual risks with likelihood, impact,
   and why they were not fixed in this path. These must be specific to
   this system (not "XSS exists in the industry").

## Required evidence

- Updated threat-model register with a status on every item from
  `as1t1-001` and later tasks (`mitigated`, `accepted`, or
  `transferred`) and a next action plus owner on any item not
  mitigated
- Dated command output of the `as1t2-002` security regression suite
  passing on the submitted commit
- A green GitHub Actions run of the `as1t2-004` workflow on that same
  commit, or a pasted log with run id
- An evidence-pack document linking to the threat model, classification
  table, regression output, CI run, secret-scan result, and header
  capture
- At least 2 accepted residual-risk write-ups with likelihood, impact,
  and why they were not fixed in this path
- Reflection note answering the task questions

Submit a repository URL plus an immutable commit or tag. Do not submit
only a slide deck or a claim that "everything is mitigated."

## Acceptance criteria

- [ ] The updated threat-model register has a status on every item
      from `as1t1-001` (`mitigated`, `accepted`, or `transferred`) and
      no item left as `open` without a next action and owner.
- [ ] The security regression suite from `as1t2-002` passes on the
      submitted commit; the command and dated output are included.
- [ ] The CI security workflow from `as1t2-004` is green on the
      submitted commit.
- [ ] An evidence-pack document links to the threat model,
      classification table, regression output, CI run, secret-scan
      result, and header capture.
- [ ] At least 2 accepted residual risks are written with likelihood,
      impact, and why they were not fixed in this path.

The mentor may pick one mitigated threat and ask you to run the
matching test, and pick one accepted risk and ask what would reopen
it. A pack with broken links or a stale suite run is not enough.

## Reflection

Answer these in your own words after doing the work:

1. Which threat changed the architecture or the API contract, and
   which one only changed a test?
2. If you had eight more hours, which accepted risk would you reopen
   first, and what evidence would tell you the fix worked?
3. What would you ask a mentor to challenge in the pack — the model,
   the suite, or a residual-risk argument?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Pick one mitigated threat and require a live suite run.
- Pick one accepted risk and ask what signal would force a reopen.
- Walk the evidence-pack links; reject broken or screenshot-only
  paths.
- Do not approve a register that still says `open` with no owner.

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
