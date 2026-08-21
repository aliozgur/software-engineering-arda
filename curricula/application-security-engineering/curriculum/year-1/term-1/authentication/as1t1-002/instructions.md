# Authentication You Can Defend

**Task ID:** `as1t1-002`  
**Estimated effort:** 12 hours  
**Module:** Authentication

## Why this task exists

The reference software-engineering path treats authentication as part of
building a production API. This task isolates authentication as something
you find, fix, and prove on a system you own: how passwords are stored,
how a session or token is revoked, and what a failed login reveals over
HTTP.

This is an apprenticeship task, not a reading checkbox. Completion requires
evidence that you can apply and explain the ideas.

## Scope rule

Work only on an application you own or a local lab you start and stop
yourself. Do not send attack traffic to any third-party host. Demonstrate
defects with requests to localhost or your own process, never to a system
you do not operate.

## Authoritative resources

- **OWASP Top 10** (primary): https://owasp.org/www-project-top-ten/
- **HTTP Semantics — RFC 9110** (deep_dive): https://www.rfc-editor.org/rfc/rfc9110

Use the linked documentation as the primary source. Prefer the RFC when
status-code or cache semantics for login responses become ambiguous.

## Work to complete

1. Continue on the application from `as1t1-001`. If authentication is
   missing, add a minimal username/password flow you control; do not
   bolt on a third-party identity provider as a way to skip this work.
2. Read the password-storage path. Record how the secret is hashed today,
   including the algorithm and whether a unique salt is used.
3. Find at least two authentication defects in this app. Typical classes:
   plaintext or reversible storage, session that survives logout, login
   error that names whether the account exists, missing brute-force
   control, token in a URL or log line. Write each finding with route or
   file location and the unsafe behaviour you observed locally.
4. Fix both defects. Put each fix in its own commit.
5. Add or update tests so that (a) the stored password is shown not to be
   plaintext or a bare SHA-2, and (b) a replayed session or token is
   rejected after logout or revocation.
6. Capture raw HTTP for one successful login and one failed login.
   Annotate status, `Set-Cookie` or `Authorization` handling, and whether
   the failed-login body differs by account existence.
7. Update the `as1t1-001` register: move the authentication threats you
   actually fixed to `mitigated`, and leave the rest open or accepted
   with a reason.

## Required evidence

- A findings note listing at least 2 authentication defects with route or
  file location, before and after behaviour
- Git history showing each fix in its own commit, not one combined
  "security" commit
- A committed test or query showing the stored password is not plaintext
  and is not a bare SHA-2 of the password
- A committed test showing that a replayed session or token is rejected
  after logout or revocation
- Captured HTTP request/response pairs for a successful login and a
  failed login
- Reflection note answering the task questions

Where code is produced, submit a repository URL plus an immutable commit
or tag reference. Do not submit only screenshots of code.

## Acceptance criteria

- [ ] Passwords are stored with a dedicated password hash (bcrypt, scrypt,
      or argon2); a committed test or query shows the stored value is not
      plaintext and is not a bare SHA-2 of the password.
- [ ] Logout or explicit revocation invalidates the session or token; a
      replay of the prior credential is rejected.
- [ ] At least 2 authentication defects found in the owned or local app
      are listed with file, line, or route, then shown fixed.
- [ ] Failed login uses the same HTTP status and body shape for an unknown
      account and a wrong password, unless the notes document a deliberate
      exception and the residual risk.
- [ ] No password, session secret, or API key is committed in any commit
      on the submitted branch.

The mentor may ask you to revoke a session live and replay the old
cookie or token. Passing a framework's default login demo without a
findings note is not enough.

## Reflection

Answer these in your own words after doing the work:

1. Why is a general-purpose hash (SHA-256 of the password) the wrong
   control here, even if it is not plaintext?
2. What HTTP status did you choose for a failed login, and which RFC 9110
   consideration (caching, intermediary reuse, or semantics of 401 versus
   403) affected that choice?
3. After logout, what exactly is invalidated — a server-side session, a
   token identifier, or only a cookie the browser was asked to drop?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to replay a revoked credential while you watch.
- Ask why 401 versus 403 was chosen on the failed-login path.
- Do not approve a submission that only enabled a library default with
  no findings note and no revocation test.

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
