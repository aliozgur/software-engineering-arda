# Authenticate and Authorize the API

**Task ID:** `be1t2-001`
**Estimated effort:** 14 hours
**Module:** Security

## Why this task exists

Term 1 built a working API that anyone who can reach it can call. That is
fine for learning HTTP and schema design. It is not fine for a service you
are about to load-test, observe, and defend. This task adds the first real
boundary around callers so later work has something to harden.

## Authoritative resources

- **HTTP Semantics - RFC 9110** (deep_dive): https://www.rfc-editor.org/rfc/rfc9110
- **OWASP Top 10** (primary): https://owasp.org/www-project-top-ten/
- **Python 3 Tutorial** (reference): https://docs.python.org/3/tutorial/

Use the linked documentation as the primary source. Prefer the RFC for
status-code choices and OWASP for the authn/authz failure modes you must
close.

## Work to complete

1. Choose an authentication method for the existing Python service (session
   cookie, bearer token, or API key) and write the choice down before you
   implement it — including what a stolen credential lets an attacker do.
2. Add at least two roles (for example owner and reader) and enforce a
   permission difference on at least one existing resource: one role can
   mutate it, the other can only read it.
3. If you store passwords, hash them with a current password-hashing
   function. Never commit a plaintext password, even in fixtures — use a
   known hash or a documented test helper that hashes at setup.
4. Keep the documented error JSON shape from Term 1. Map auth failures to
   401 and authorization failures to 403. Do not collapse them.
5. Update the OpenAPI document with the security scheme and mark every
   protected route.
6. Write automated tests for the three callers on the same protected
   resource: anonymous, authenticated-but-forbidden, and authorized.
7. Confirm application logs never print tokens, passwords, or session
   secrets. Fix any logger that does.

Commit the design note, the implementation, the OpenAPI change, and the
tests as separate commits. A single "add auth" dump will be sent back.

## Required evidence

- Git history showing auth, role checks, and tests added in separate
  commits, not one dump
- Automated test output showing a 401, a 403, and a 200 for the same
  protected resource under three callers
- The OpenAPI document with a declared security scheme and protected
  routes marked
- A README section naming the auth method, the roles, and the exact
  permission on at least one resource
- A grep or dump proving stored credentials are hashed and that tokens
  or passwords do not appear in application logs

Submit a repository URL plus a commit reference. Do not submit only
screenshots of code.

## Acceptance criteria

- [ ] An unauthenticated request to a protected route returns 401 with
      the documented error JSON shape.
- [ ] An authenticated caller without permission on that resource
      returns 403, not 401 or 404.
- [ ] A stored password, if passwords are used, appears only as a hash
      in the database dump or fixture — never as plaintext.
- [ ] The OpenAPI document declares the security scheme and marks every
      protected route as requiring it.

The mentor may ask you to call a protected route with a forged or expired
credential live, and to point at the exact check that rejects it.

## Reflection

Answer these in your own words after doing the work:

1. What can an attacker do with a stolen credential of each role you
   implemented?
2. Why did you choose 403 rather than 404 for a forbidden resource —
   and when would you choose the other?
3. Which OWASP Top 10 item did this task actually close, and which one
   is still open on this service?

Also record:

- What took longer than expected?
- What would you change about the auth method if a third role appeared
  next week?
- What remains unclear?

## Mentor review guide

- Ask the apprentice to call a protected route with a missing token, an
  expired/invalid token, and a valid token for the weaker role — live.
- Confirm 401 and 403 are not treated as the same case in code or docs.
- Reject a submission that logs Authorization headers or stores a
  plaintext password in a fixture.

Suggested review outcome: **Approve**, **Request revision**, or **Create
follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes.
Solution generation is not the intended path for this task. Material AI
assistance must be disclosed with the provider/model (if known), purpose,
and verification performed.

## Completion gate

This task is complete only once the evidence is submitted and the mentor
approves the demonstrated boundary — not when login merely "works on my
machine."
