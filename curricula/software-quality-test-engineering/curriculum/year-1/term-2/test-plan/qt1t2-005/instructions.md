# Write a Test Plan a Mentor Would Actually Sign Off On

**Task ID:** `qt1t2-005`  
**Estimated effort:** 20 hours  
**Module:** Test plan

## Why this task exists

This is the artifact that separates someone who can write tests from someone
who can be trusted to decide what testing a real change needs, which is the
skill this curriculum has been building toward.

This is an apprenticeship task, not a content-consumption checkbox. A generic
checklist reused across changes is not a plan.

## Authoritative resources

No single official document is the source of truth for this task. Reuse the
primary documentation of the tools you already applied in this curriculum
(Pact, Stryker, k6, your CI platform) where the plan names those gates. If
you consult extra material, record it in your learning notes and prefer
primary documentation over tutorial aggregation sites.

## Work to complete

1. Pick a real, nontrivial upcoming change on a system you control — a
   behavior change, a migration, an API revision — not "add a README." Write
   the plan for *that* change.
2. Write the test plan so it names:
   - specific risks for this change
   - the test layers you will use
   - which existing quality gates apply and which you explicitly skip, with
     a reason for each
   - at least two test cases you are excluding, and why
3. Implement and pass at least the top two or three highest-risk tests named
   in the plan. The plan is not finished when it is only a document.
4. Put the plan through review. Mentorship is optional in this curriculum, so
   the reviewer may be a mentor, a peer, or a structured self-review written
   as if you were handing the plan to someone who will ship without you. The
   review must produce at least one documented change to the plan (a risk
   added, a gate un-skipped, an exclusion reversed). A rubber-stamp "looks
   good" with no edit does not count.
5. Be ready to defend what would make *you* confident enough to ship — not
   what would make a tool green.

## Required evidence

- The written test plan, naming risks, layers, gates applied/skipped and
  explicit exclusions
- Commits implementing the highest-risk tests from the plan, passing
- A record of the plan review and what changed as a result of it
- A reflection note answering the task's questions

Submit a repository URL plus the plan and the review record. Do not submit
only a passing suite with no plan.

## Acceptance criteria

- [ ] The plan names specific risks for this specific change, not a generic
      checklist reused across changes.
- [ ] The plan states which existing quality gates apply and which are
      explicitly skipped, with a reason for each.
- [ ] At least 2 explicitly excluded test cases are named along with the
      reason for excluding them.
- [ ] At least the top 2-3 highest-risk tests named in the plan are
      implemented and passing.
- [ ] A record exists of at least one change made to the plan as a result of
      review.

The mentor may ask you to ship with one named gate skipped and explain what
you are accepting. A complete-looking template with no implemented tests is
not enough.

## Reflection

Answer these in your own words after doing the work:

1. What would make you, not a tool, confident enough to ship this change?
2. Which exclusion would you be least comfortable defending to the person
   who owns the incident if that case failed in production?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to defend one skipped gate and one excluded case without
  rereading the plan.
- Do not approve a generic checklist, or a review record that changed no
  words in the plan.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, quizzes and coaching. Solution
generation is not the intended path for this task. The apprentice must be
able to explain, modify, test and defend every submitted artifact. Material
AI assistance must be recorded in the submission notes with the
provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the
evidence is submitted and the mentor approves the demonstrated competency.
