# CSRF, Cookies and Unsafe Methods

**Task ID:** `as1t2-001`  
**Estimated effort:** 10 hours  
**Module:** Csrf

## Why this task exists

Cookie-authenticated applications will send credentials on requests the
user did not mean to make. This task asks you to inventory state-changing
routes on the app you operate, pick a CSRF control you can explain, set
cookie flags deliberately, and prove that a request missing that control
is rejected.

This is an apprenticeship task, not a reading checkbox. Completion requires
evidence that you can apply and explain the ideas.

## Scope rule

Work only on an application you own or a local lab you start and stop
yourself. Simulate a "cross-site-style" request locally (missing token,
or a request you craft without the app's CSRF header). Do not send
forged requests to any third-party host.

## Authoritative resources

- **OWASP Top 10** (primary): https://owasp.org/www-project-top-ten/
- **HTTP Semantics — RFC 9110** (deep_dive): https://www.rfc-editor.org/rfc/rfc9110

Use RFC 9110 when deciding whether a method is safe or idempotent.
PortSwigger CSRF articles may be used as free reading only.

## Work to complete

1. List every documented route that changes state. For each, record the
   HTTP method. If any GET changes state, move that change to POST,
   PUT, PATCH, or DELETE.
2. Choose one CSRF control for cookie-authenticated routes: a
   synchronizer token (or double-submit cookie) checked server-side, or
   `SameSite=Strict` on the session cookie. Write why you chose it for
   this app. Bearer-token APIs that do not use cookies still need the
   notes to say why CSRF does not apply, and must still set cookie
   flags correctly if any cookie remains.
3. Implement the control so a request that lacks it is rejected.
4. Set session cookies to `HttpOnly` and `SameSite` (`Strict` or `Lax`,
   named). Set `Secure` unless the local lab is HTTP-only; if so, write
   that as residual risk.
5. Write a committed test or scripted local request that omits the
   token (or otherwise represents a cross-site-style call) and is
   rejected. Record the command and status.
6. Update the threat-model register.

## Required evidence

- A findings note listing each state-changing route, the CSRF control
  used (token or SameSite=Strict, named), and cookie flags observed
  before and after
- Git history showing cookie-flag changes and CSRF enforcement in
  separate commits
- A committed test or scripted local request showing a missing-token
  or cross-site-style request rejected
- A captured `Set-Cookie` header after login showing `HttpOnly` and
  `SameSite`, plus `Secure` or a residual-risk note for HTTP-only
  local labs
- Reflection note answering the task questions

Where code is produced, submit a repository URL plus an immutable commit
or tag reference. Do not submit only screenshots of code.

## Acceptance criteria

- [ ] Every documented state-changing route (POST, PUT, PATCH, or
      DELETE) rejects a request that lacks the CSRF token or the
      equivalent SameSite=Strict cookie defense; the notes name which
      control is used.
- [ ] Session cookies set HttpOnly and SameSite (Strict or Lax, named
      in the notes); Secure is set, or the notes record that the local
      lab is HTTP-only and name that as residual risk.
- [ ] No documented GET route changes application state.
- [ ] A committed test or scripted request to the local app shows a
      missing-token or cross-site-style request rejected.

The mentor may omit the token on a live request and ask you to predict
the status before it is sent. A client-only token that the server does
not check is not enough.

## Reflection

Answer these in your own words after doing the work:

1. Why does `SameSite=Lax` still allow a CSRF-shaped request on some
   top-level navigations, and did you accept that?
2. Why is changing state on GET a CSRF problem even if you also have a
   token on POST?
3. If you used a Bearer token in `Authorization` and no cookies, why
   is classic CSRF a different threat — and what did you still check?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Omit the CSRF control on a live local request and compare the
  result to the notes.
- Ask whether `SameSite` is a complete substitute for a token in this
  app's browser support matrix.
- Do not approve GET handlers that increment counters, send mail, or
  delete records.

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
