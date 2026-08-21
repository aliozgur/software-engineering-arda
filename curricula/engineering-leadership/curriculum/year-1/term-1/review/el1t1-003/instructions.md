# Review Notes That Teach Without Taking the Keyboard

**Task ID:** `el1t1-003`
**Estimated effort:** 8 hours
**Module:** Review

## Why this task exists

Leads often "save time" by rewriting the junior's pull request. CI goes green. The junior does not learn. The next change comes back with the same class of miss. Written review comments that distinguish **blocking** from **advisory**, that ask at least one real question, and that keep your preferred patch in a *separate* note are the inspectable version of mentoring-through-review.

This is an apprenticeship task. Reading about staff-plus teaching is preparation. Completion requires comments on the given change — not a claim that you "usually give good feedback."

## Authoritative resources

- **Staff Engineer (Will Larson)** (primary): https://staffeng.com/ — read the material on growing other engineers and on doing work that does not require you to be in the critical path. Record extra sources in your notes.

## Scenario

**Priya** opened `PR-1847` on Harborline Checkout: "Handle webhook retries for payment.updated." You are the reviewer. Review **this** diff. Do not substitute a different PR unless you also paste the exact diff you reviewed (so a mentor can open the same text).

```python
# checkout/webhooks.py  (Priya, PR-1847)
import os
import requests

WEBHOOK_SECRET = "whsec_live_9f3a"  # TODO: move later
RETRY_URL = os.getenv("RETRY_URL", "http://identity.internal/v1/retry")

def handle_payment_updated(payload):
    # I cleaned up some names while I was here
    evt_id = payload.get("id") or payload.get("event_id")
    try:
        resp = requests.post(
            RETRY_URL,
            json={"event": evt_id, "secret": WEBHOOK_SECRET},
            timeout=None,
        )
        if resp.status_code >= 500:
            return True  # caller can retry
        return resp.ok
    except Exception:
        print("webhook failed")
        return True

def handle_payment_updated_v2(payload):
    # old path, keep for now
    return handle_payment_updated(payload)
```

Priya's PR description: "Adds retry. Tested locally once. Also renamed a helper. No tests yet — will add if needed."

Known team rules (write as if they are real): webhook secrets must not be in source; outbound calls must have a finite timeout; swallowed exceptions must be logged with the event id; drive-by refactors need their own PR or an explicit note.

## Work to complete

1. Write at least **four** inline comments tied to a line or symbol in the diff (`WEBHOOK_SECRET`, `timeout=None`, `except Exception`, `handle_payment_updated_v2`, missing tests, or similar). Label **every** comment `blocking` or `advisory`.
2. At least one comment must be a **question** that does not contain the fix (no pasted corrected function, no "change this to `timeout=5`"). The question should force Priya to choose.
3. Write an author-facing summary: at least three requested changes, and **exactly one** explicit non-issue (something that is fine to leave in this PR).
4. In a **separate** file (`reviewer-patch.md` or similar), write the change *you* would have made if you were the author — including the secret, timeout, and error-handling choices. Then write one paragraph stating **why you did not paste that patch into the review comments**.
5. Commit the review notes and the separate patch note as distinct files. Do not commit a rewritten `webhooks.py` as the submission; the teaching artifact is the review.

## Required evidence

- Review notes on the provided Harborline diff with at least four comments, every comment labeled blocking or advisory
- At least one comment that is a question and does not contain the fix
- A separate reviewer-patch note that states the change the reviewer would have made and why it was not pasted into the review
- An author-facing summary with at least three requested changes and exactly one explicit non-issue

Submit a repository URL plus a commit reference.

## Acceptance criteria

- [ ] Every inline comment is labeled blocking or advisory, and there are at least four comments.
- [ ] At least one comment is a question whose text does not include the patched code or the exact fix.
- [ ] A separate note lists the change the reviewer would have written and states why it was withheld from the review comments.
- [ ] The author-facing summary names at least three requested changes and exactly one thing that should not be changed in this PR.

## Reflection

Answer in your own words after doing the work:

1. Which comment would you still rewrite if Priya asked "just tell me what to type"?
2. What did you mark as the non-issue, and what would make it blocking on a later PR?

Also record: what took longer than expected, what you would practice again, what remains unclear, and which artifact best proves you reviewed instead of taking the keyboard.

## Mentor review guide

- Ask the apprentice to point at the question-comment and say what answer would change the review. If no answer would change it, it was a leading question.
- Do not approve a review that pastes a full replacement function into the comments, or that labels a secret-in-source issue as advisory without a stated exception.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**.

## AI use policy

Mode: **guided**. AI may explain what blocking versus advisory means, offer hints if you are stuck naming a non-issue, and quiz you on review hygiene. AI must not generate the comment set, the summary, or the withheld patch for you. Disclose any material AI use with provider/model (if known), purpose, and verification.

## Completion gate

This task is not complete when the diff "would be fine if you merged your own rewrite." It is complete when Priya could land the change from your comments alone, and a mentor can see that you chose not to type it for them.
