# Write the Recommendation You Would Sign

**Task ID:** `el1t2-004`
**Estimated effort:** 6 hours
**Module:** Ethics

## Why this task exists

Harborline will ask you to ship something that is probably legal and still a professional problem. "I would push back" is not evidence. A memo you would sign, a stakeholder note that leads with the recommendation, and an escalation path that names a role and an attachment are.

This is an apprenticeship task. Reading the ACM Code is preparation. Completion requires citations by section, not a general ethics essay.

## Authoritative resources

- **ACM Code of Ethics** (primary): https://www.acm.org/code-of-ethics — use the numbered principles. Cite at least two by number or official title (for example, 1.6 / "Respect privacy", 2.5 / "Give comprehensive and thorough evaluations"). Prefer the Code over summary blogs.

## Scenario

Product (not engineering) asks Checkout to **keep raw `payment.updated` webhook bodies, including payer email and last-four, for 18 months** to "train a fraud model." The current privacy notice says payment-adjacent data is retained for **90 days** for payment operations, then deleted or aggregated. Legal has not signed off. The vendor offering the model wants a sample export "to see if it is worth a contract." Morgan says: "If we say no, we look difficult. Can you just turn the flag on in staging with a copy of prod?"

You are the tech lead. You must recommend one of:

- **Ship as asked** (18-month raw retention + vendor sample)
- **Ship with a change** (you specify the change)
- **Refuse** the ask as stated

You may not invent a law that forbids it. The task is professional judgment under the ACM Code, including the case where the law is quiet and the notice is not.

## Work to complete

1. Write a decision memo: context, recommendation, and at least **two** ACM Code sections cited by **number or official title**, each tied to a sentence in your reasoning.
2. Write an **options table** with at least **three** options (the three bullets above, or your own third). Each row: option, who is harmed if you pick it, **concrete** harm (a notice violation, a vendor holding emails, a model trained on people who did not consent — not "it feels wrong").
3. Write the **stakeholder note** you would send to Product/Morgan: **≤200 words**, recommendation in the **first 40 words**.
4. Write an **escalation path** if you are overruled: a named **role** (Morgan's manager, Harborline privacy counsel, the DRI on the privacy notice — pick one that exists in a normal company) and the **document you would attach** (this memo, the notice excerpt, the Code citations).
5. Commit memo, table, note, and escalation as files. If you compress them into one Markdown file, use headings a mentor can check independently.

## Required evidence

- A decision memo that cites at least two ACM Code of Ethics sections by their number or official title
- An options table with at least three options, each naming a harmed party and a concrete harm
- A stakeholder note of at most 200 words that states the recommendation in the first 40 words
- An escalation path that names a role and the document you would attach if overruled

Submit a repository URL plus a commit reference.

## Acceptance criteria

- [ ] The memo cites at least two ACM Code sections by number or official title.
- [ ] The options table has at least three options; each row names a harmed party and a concrete harm.
- [ ] The stakeholder note is at most 200 words and states the recommendation in the first 40 words.
- [ ] The escalation path names a role (not "someone in legal") and the file or memo you would attach.

## Reflection

Answer in your own words after doing the work:

1. Which ACM section did the most work in your recommendation, and which one was decorative?
2. If Morgan said "legal will catch it later," what sentence in your note still holds?

Also record: what took longer than expected, what you would practice again, what remains unclear, and which artifact you would still sign in a year.

## Mentor review guide

- Count ACM citations. If they are "the Code says be ethical" without a number or title, request revision.
- Read only the first 40 words of the stakeholder note. If the recommendation is not there, request revision.

Suggested review outcome: **Approve**, **Request revision**, or **Discuss live**.

## AI use policy

Mode: **guided**. AI may explain a numbered ACM principle, offer hints if a harm is still an adjective, and quiz you on the difference between legal minimum and professional duty. AI must not write the memo, the table, the note, or the escalation path for you. Disclose any material AI use with provider/model (if known), purpose, and verification.

## Completion gate

This task is not complete when you "thought about ethics." It is complete when a mentor can check the citations, the harms, and the first 40 words without asking what you meant.
