# Wire Quality Gates into the Pipeline

**Task ID:** `qt1t1-005`  
**Estimated effort:** 16 hours  
**Module:** Quality gates

## Why this task exists

A pipeline that runs tests but enforces no threshold lets quality drift
silently. A gate that actually blocks a merge is the mechanism that makes a
quality standard stick.

This is an apprenticeship task, not a content-consumption checkbox. A pipeline
that only prints reports is not a gate.

## Authoritative resources

- **GitHub Actions Documentation** (reference): https://docs.github.com/actions
- **GitLab CI/CD Documentation** (reference): https://docs.gitlab.com/ci/

Pick whichever platform hosts your repository. Use the official documentation as
your primary source; if you use other material, record it in your notes and
prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Start from a repository with a real test suite (the work from earlier tasks
   in this term is a good base).
2. Add three gates that fail the build, not just warn:
   - a lint or static-analysis gate
   - a coverage-threshold gate
   - one deeper test-quality gate (mutation score, contract verification, or
     flake-detection from `qt1t1-004`)
3. For each gate, introduce a deliberate violation in its own commit, capture
   the pipeline failing for that reason, then revert the violation and capture
   the pipeline passing again. Three independent fail/pass pairs — do not
   violate all three at once.
4. Write a threshold-justification note. Each number (coverage floor, mutation
   floor, lint level) needs a reason tied to this codebase, not "the tool
   defaulted to 80."
5. Commit the CI configuration that enforces all three gates.

## Required evidence

- The committed CI configuration file(s) showing all three gates
- Pipeline run logs or links showing each gate individually failing on a
  deliberate violation
- Pipeline run logs or links showing the pipeline passing once each violation
  is reverted
- A written threshold-justification note

Submit a repository URL plus pipeline run links or logs. Do not submit only a
screenshot of a green check.

## Acceptance criteria

- [ ] The CI configuration includes a lint/static-analysis gate that fails the
      build, a coverage-threshold gate, and one additional test-quality gate.
- [ ] Each of the three gates is shown individually failing a deliberately
      introduced violation.
- [ ] Each gate is shown passing again once the corresponding violation is
      reverted.
- [ ] Each threshold has a written justification, not left at a tool's default
      with no comment.

The mentor may lower one threshold in review and ask what regressions that
would start letting through. A green pipeline alone is not proof.

## Reflection

Answer these in your own words after doing the work:

1. Which gate would you drop first if the pipeline became too slow, and what
   risk would that accept?
2. What is the smallest violation that still fails each gate — and did you
   actually try one that small?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to break one gate live and predict the job name and
  failure text before pushing.
- Do not approve gates that warn-only, or thresholds copied from a tutorial
  with no justification.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the
intended path for this task. The apprentice must be able to explain, modify, test
and defend every submitted artifact. Material AI assistance must be recorded in the
submission notes with the provider/model (if known), purpose, and verification
performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the
evidence is submitted and the mentor approves the demonstrated competency.
