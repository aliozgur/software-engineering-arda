# Review a Peer's Pull Request

**Task ID:** `ef1t2-001`
**Estimated effort:** 4 hours
**Module:** Code Review

## Why this task matters

Writing code and reviewing code are different skills. A review full of vague praise ("looks good!") or vague criticism ("this feels off") wastes the author's time either way — they can't act on either one. This task asks you to practice feedback that is specific enough to act on, and delivered the way you'd want to receive it yourself.

## Authoritative resource

- **Pro Git** (reference): https://git-scm.com/book/en/v2

## What you'll do

1. Find a real, non-trivial pull request to review: a peer's, one your mentor assigns, or an open PR on a small open-source project that's still awaiting review.
2. Leave at least 5 review comments, each tied to a specific line or section — not a general comment on the whole PR.
3. For each comment, be clear (in the comment itself or in a note alongside it) whether it's **blocking** (must be addressed before merge), a **suggestion** (optional improvement), or a **question** (you're checking your own understanding, not demanding a change).
4. Make sure at least one comment is grounded in something concrete: a specific test, a stated acceptance criterion, or an observed behavior — not only naming style or formatting.
5. If you disagree with something, phrase it as a suggested alternative or a genuine question about the author's reasoning, not just a flat "this is wrong."

## Evidence to submit

- A link to the reviewed PR with your comments visible, or the written review text if commenting directly wasn't possible.
- A short self-review note classifying each comment as blocking, suggestion, or question, in one place.
- An AI disclosure entry if AI helped draft review comments.

## Acceptance criteria

- [ ] At least 5 review comments exist on the actual PR (or a written substitute), each tied to a specific line or section.
- [ ] Each comment is labeled or clearly distinguishable as blocking, suggestion, or question.
- [ ] At least one comment references a specific acceptance criterion, test, or behavior, not only style.
- [ ] No comment is purely negative without a suggested alternative or a question inviting the author's reasoning.

## Reflection

1. Which comment was hardest to phrase constructively, and how did you end up phrasing it?
2. If you received this exact review on your own PR, which comment would you find most useful, and why?

## Mentor review guide

- Count comments and check each is tied to a line or section, not a general "looks good."
- Confirm every comment is labeled blocking, suggestion, or question.
- Do not approve a review that only nits naming or formatting.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI assistance for this task

Mode: **guided**. You may ask an AI assistant to help you word a difficult comment more constructively. Having AI generate the substance of the review — deciding what's actually wrong with the code — is not allowed; the technical judgment has to be yours.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and a mentor — or a documented self-check against every acceptance criterion, if you are working without one — confirms the demonstrated competency.
