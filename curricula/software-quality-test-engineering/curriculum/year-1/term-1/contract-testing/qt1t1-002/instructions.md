# Contract Testing Across a Service Boundary

**Task ID:** `qt1t1-002`  
**Estimated effort:** 14 hours  
**Module:** Contract testing

## Why this task exists

Integration bugs between services are expensive precisely because unit tests on
either side can pass while the two sides disagree about the interface. Contract
tests catch that disagreement without needing both services running together.

This is an apprenticeship task, not a content-consumption checkbox. Reading Pact
docs is only preparation. Completion requires a contract that actually fails when
the provider breaks.

## Authoritative resources

- **Pact Documentation** (primary): https://docs.pact.io/

Use the official Pact documentation as the primary source. You may use additional
sources, but record them in your learning notes and prefer primary documentation
over tutorial aggregation sites.

## Work to complete

1. Pick one real service boundary you control on at least one side — HTTP or
   message — with a consumer that expects a specific request/response (or message)
   shape and a provider that is supposed to honor it. Two in-process functions
   calling each other do not count.
2. Write consumer-driven contract tests that generate a contract covering at least
   four distinct interactions. At least one interaction must be an error response
   (or a failure message), not only happy-path payloads.
3. Verify that contract against the provider with a single documented command.
   Capture the passing verification output.
4. Introduce a deliberate provider break that a provider-side unit test would not
   necessarily notice (rename a field the consumer reads, change a status code,
   drop a required header). Capture the failing verification output.
5. Revert or fix the break. Capture verification passing again.
6. In your reflection, name the specific disagreement the contract caught that a
   provider-side unit test of the same handler would have missed.

## Required evidence

- The committed contract file(s), or an accessible Pact broker export
- A commit showing contract verification passing
- A commit or log showing verification failing after a deliberate provider break,
  and passing again after the fix
- A reflection note answering what the contract test caught that a provider-side
  unit test would not have

Where code is produced, submit a repository URL plus an immutable commit or tag
reference when possible. Do not submit only screenshots of a green verification.

## Acceptance criteria

- [ ] The committed contract covers at least 4 distinct interactions, including at
      least one error response.
- [ ] A single command verifies the contract against the provider.
- [ ] A deliberate provider break is shown causing contract verification to fail,
      with the failure output captured.
- [ ] Verification passes again after the break is reverted, evidenced by a
      follow-up commit or log.

The mentor may ask you to break a different field live and predict the failure
before running verification. Passing verification alone is not proof.

## Reflection

Answer these in your own words after doing the work:

1. What did the contract test catch that a provider-side unit test of the same
   handler would not have caught?
2. Which interaction was the hardest to specify, and what did you almost leave
   implicit?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to change one field the consumer actually reads and explain
  whether consumer tests, provider tests, or the contract should fail first.
- Do not approve a contract that only restates a happy-path OpenAPI snippet with
  no error interaction.

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
