# XSS and Output Encoding

**Task ID:** `as1t1-005`  
**Estimated effort:** 10 hours  
**Module:** Xss

## Why this task exists

The reference software-engineering lab asks you to write cause-to-prevention
notes for XSS. This task asks you to locate a sink in the app you operate,
show unescaped markup on localhost, encode for the correct context, and
keep a test that fails when that encoding is removed. CSP is added as
defense in depth, not as the only control.

This is an apprenticeship task, not a reading checkbox. Completion requires
evidence that you can apply and explain the ideas.

## Scope rule

Work only on an application you own or a local lab you start and stop
yourself. Do not load XSS payloads against any third-party host. Use
PortSwigger Academy as free reading only — do not run its hosted labs
for this task.

## Authoritative resources

- **OWASP Top 10** (primary): https://owasp.org/www-project-top-ten/
- **PortSwigger Web Security Academy** (reading only):
  https://portswigger.net/web-security/cross-site-scripting

Read the XSS articles to learn contexts and encoding rules. Do not
complete hosted labs or send payloads to PortSwigger infrastructure.

## Work to complete

1. Read the PortSwigger XSS overview and the pages on reflected versus
   stored XSS, and on encoding contexts, as background only.
2. Find a reflected or stored sink in your owned or local app where
   request or stored data is written into HTML without encoding. If none
   exists, seed one temporary local sink on a branch, document it, then
   fix it.
3. On localhost only, submit input that would become markup if left
   unescaped (for example a tagged string). Record the response body
   showing the unescaped output. Do not target any other origin.
4. Fix the sink with context-appropriate encoding or by enabling the
   framework auto-escape that actually covers this context. Name the
   context in the notes: HTML body, attribute, URL, or JavaScript.
5. Write a committed test that fails when encoding is removed and
   passes with encoding in place. Record the command and both outputs.
6. Set `Content-Type` on HTML responses to include `charset=utf-8`.
   Add a `Content-Security-Policy` that does not include `unsafe-inline`
   for scripts, or write a residual-risk paragraph explaining what still
   allows inline script and why it remains this term.
7. Update the threat-model register.

## Required evidence

- A findings note naming the sink, whether it is reflected or stored,
  the encoding context (HTML body, attribute, URL, or JavaScript), and
  a local request that showed unescaped markup before the fix
- Git history showing the encoding fix and the CSP or residual-risk
  note in separate commits
- A committed test that fails when encoding is removed from the sink
  and passes with encoding in place, with command and both outputs
- A captured HTML response that includes Content-Type with charset=utf-8
  and the Content-Security-Policy header or the residual-risk paragraph
- Reflection note answering the task questions

Where code is produced, submit a repository URL plus an immutable commit
or tag reference. Do not submit only screenshots of code.

## Acceptance criteria

- [ ] At least 1 reflected or stored XSS sink is identified and shown, on
      the local app only, producing unescaped attacker-controlled markup
      before the fix.
- [ ] The fix uses context-appropriate encoding or a framework auto-escape
      that is actually enabled; the notes name the context as HTML body,
      attribute, URL, or JavaScript.
- [ ] Responses that contain HTML declare a Content-Type that includes
      charset=utf-8.
- [ ] A Content-Security-Policy is set that does not include
      `unsafe-inline` for scripts, or the notes record why a stricter
      policy is not yet possible and what residual risk remains.
- [ ] A committed test fails when encoding is removed from the fixed sink
      and passes with encoding in place; command and both outputs are
      recorded.

The mentor may ask you to name the wrong encoding for a different
context (attribute versus JavaScript) and what would break. A global
"strip tags" filter without a named context is not enough.

## Reflection

Answer these in your own words after doing the work:

1. Why are input validation and output encoding different controls, and
   which one actually closed your sink?
2. What would `unsafe-inline` still allow an attacker to do if encoding
   failed on one remaining page?
3. Reflected versus stored: which did you find, and what extra step
   does the stored case require in a test?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to pick the encoding function for an attribute
  context and for a JavaScript string context without notes.
- Confirm the proving test was run after removing encoding, not only
  after adding it.
- Do not approve a CSP-only submission that left the sink unescaped.

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
