# Write a Pull Request Description a Reviewer Can Act On

**Task ID:** `ef1t1-006`
**Estimated effort:** 4 hours
**Module:** Professional Practice

## Why this task matters

A PR description that just says "fixes bug" or "updates code" forces every reviewer to reverse-engineer your intent from the diff before they can even start reviewing it properly. A description that states the problem, the change, and how it was verified is a professional courtesy — and it gets your own work reviewed faster, because the reviewer isn't guessing.

## Authoritative resource

- **Pro Git** (reference): https://git-scm.com/book/en/v2

## What you'll do

1. Take a real change you already made — reuse the pull request from `ef1t1-002`, or a new small one — and write (or rewrite) its description.
2. Structure it around: the problem being solved (stated before the change itself), what actually changed, how you verified it (a specific test run or manual step, not "tested it"), and anything you deliberately left out of scope.
3. Ask someone who has not seen the diff — a peer, a mentor, or anyone willing — to read only the description and tell you what they think changed and how they'd verify it. If no one is available, wait at least a few hours, then try to reconstruct the change from the description alone without opening the diff; record what you missed.
4. Compare what they (or you) said to what you actually intended. Note any mismatch.

## Evidence to submit

- The PR description text: a link plus the raw text, since descriptions can be edited later.
- A short note recording what your reader said after reading only the description, and whether it matched your intent.
- An AI disclosure entry if AI helped draft any part of the text.

## Acceptance criteria

- [ ] The description states the problem being solved before describing the change.
- [ ] The description names at least one concrete verification step actually performed, not just "tested it".
- [ ] The description names anything intentionally left out of scope or deferred.
- [ ] A reader who has not seen the diff can describe, after reading only the description, what changed and how to verify it — confirmed in your submitted note.

## Reflection

1. What did your reader misunderstand, and what in the description caused that?
2. What's the shortest version of this description that would still pass the acceptance criteria above?

## Mentor review guide

- Cover the diff and read only the description. If you cannot say what changed and how to verify it, request revision.
- Check that the named verification step is specific (a command, a file, a case) — "tested it" is not enough.
- Mentorship is optional here: a delayed self-read of the description is acceptable if the note records what was missed.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI assistance for this task

Mode: **guided**. Explanations and hints about what makes a description clear are allowed. Having AI draft the description for you is not — you have to be able to defend every claim in it, including the verification steps.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and a mentor — or a documented self-check against every acceptance criterion, if you are working without one — confirms the demonstrated competency.
