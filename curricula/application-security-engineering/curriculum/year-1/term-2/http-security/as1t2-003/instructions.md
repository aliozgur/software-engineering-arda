# HTTP Security Headers and CORS as a Contract

**Task ID:** `as1t2-003`  
**Estimated effort:** 8 hours  
**Module:** Http security

## Why this task exists

Security headers and CORS are HTTP, not folklore. This task asks you to
set a small, named set of headers on the app you operate, forbid a
wildcard origin on credentialed routes, and capture the bytes a browser
would see. RFC 9110 is the reference for what a header means; OWASP
tells you which browser threats the header is meant to reduce.

This is an apprenticeship task, not a reading checkbox. Completion requires
evidence that you can apply and explain the ideas.

## Scope rule

Send header and CORS probes only to the application you own or the
local lab you operate. Do not probe third-party origins.

## Authoritative resources

- **HTTP Semantics — RFC 9110** (deep_dive):
  https://www.rfc-editor.org/rfc/rfc9110
- **OWASP Top 10** (primary): https://owasp.org/www-project-top-ten/

Use the RFC for header and method semantics. Use OWASP for the class
of weakness a missing header leaves open.

## Work to complete

1. Capture a current HTML response and a current API response. List
   which of the following are already present: `X-Content-Type-Options`,
   `Referrer-Policy`, `Content-Security-Policy` / `X-Frame-Options`,
   CORS headers.
2. Set `X-Content-Type-Options: nosniff` and a `Referrer-Policy` (name
   the policy, for example `strict-origin-when-cross-origin`) on HTML
   responses.
3. Add a frame-busting control: `X-Frame-Options` or CSP
   `frame-ancestors`. If CSP already exists from `as1t1-005`, extend it
   rather than inventing a second policy.
4. Configure CORS. Credentialed routes must not return
   `Access-Control-Allow-Origin: *`. Allowed origins are an explicit
   list. If the app is same-origin only, document that and still
   capture a request that would have needed CORS.
5. Write a table: header or CORS field, threat reduced, request used
   to demonstrate it (method, path, and any `Origin` you sent locally).
6. Update the threat-model register.

## Required evidence

- A header-and-CORS table listing each header or CORS field, the
  threat it reduces, and the request used to capture it
- Captured HTTP responses showing `X-Content-Type-Options`,
  `Referrer-Policy`, and the frame-busting control on an HTML route
- Captured CORS preflight or response on a credentialed route showing
  an explicit origin list and no `Access-Control-Allow-Origin: *`
- Git history showing header defaults and CORS configuration in
  separate commits
- Reflection note answering the task questions

Where configuration is produced, submit a repository URL plus an
immutable commit or tag reference. Do not submit only screenshots of
browser devtools without the raw headers.

## Acceptance criteria

- [ ] Every HTML response includes `X-Content-Type-Options: nosniff`
      and a `Referrer-Policy`, shown in a captured response.
- [ ] No credentialed route returns `Access-Control-Allow-Origin: *`;
      allowed origins are an explicit list in configuration or code.
- [ ] A frame-busting control is present (`X-Frame-Options` or CSP
      `frame-ancestors`), shown in a captured response.
- [ ] A notes table lists each header, the threat it reduces, and one
      request that demonstrates it.

The mentor may send a local request with `Origin: https://evil.example`
and ask what the app must return. A framework default you cannot name
is not enough.

## Reflection

Answer these in your own words after doing the work:

1. What does `nosniff` prevent that `Content-Type` alone does not?
2. Why is `Access-Control-Allow-Origin: *` incompatible with
   credentialed requests, and did any route in this app still emit it
   before the fix?
3. Which header in your table is defense in depth for a control you
   already implemented (encoding, CSRF), and which is the only control
   for its threat?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Send a local request with a foreign `Origin` and compare the
  response to the table.
- Ask the apprentice to explain `Referrer-Policy` without saying
  "it's more secure."
- Do not approve `*` on a route that sets cookies or uses
  `Authorization` plus `Access-Control-Allow-Credentials: true`.

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
