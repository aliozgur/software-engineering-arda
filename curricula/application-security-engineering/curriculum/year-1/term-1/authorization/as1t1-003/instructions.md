# Authorization and Object-Level Access

**Task ID:** `as1t1-003`  
**Estimated effort:** 12 hours  
**Module:** Authorization

## Why this task exists

The reference software-engineering path asks that authorization be
enforced server-side on a production API. This task goes further: you
must find an object-level failure (or introduce a local one you then
remove) and prove, with two users you control, that user A cannot act on
user B's object. You also separate horizontal privilege from vertical
privilege in writing, using examples from this system.

This is an apprenticeship task, not a reading checkbox. Completion requires
evidence that you can apply and explain the ideas.

## Scope rule

Work only on an application you own or a local lab you start and stop
yourself. Create two local users on that app. Do not attempt to access
anyone else's account or any third-party host.

## Authoritative resources

- **OWASP Top 10** (primary): https://owasp.org/www-project-top-ten/
- **HTTP Semantics — RFC 9110** (deep_dive): https://www.rfc-editor.org/rfc/rfc9110

PortSwigger's access-control *articles* may be used as free reading
(`https://portswigger.net/web-security/access-control`). Do not run
hosted labs or send attack traffic to PortSwigger or any other
third-party host; reproduce checks only against the app you operate.

## Work to complete

1. Create two local users (A and B) that each own at least one object
   addressable by an identifier in the URL or request body.
2. For every documented object-id route (read, update, delete), send the
   request as user A using user B's identifier. Record status, body, and
   whether user B's data appeared. This is a check on *your* lab, not a
   hunt across other systems.
3. Find at least two authorization defects. If the current code already
   denies cross-user access everywhere, seed a temporary local defect on
   a branch, document it, then fix it — the point is the find/fix/prove
   loop, not a claim that the app was born secure.
4. Fix both defects server-side. Hiding a button is not a fix. Put each
   fix in its own commit.
5. Add a committed test: user A cannot read, update, or delete user B's
   object through the documented object-id route.
6. Capture three HTTP exchanges for the same privileged route:
   unauthenticated, authenticated-but-unauthorized, and authorized.
   Record the status pair you chose and justify it against RFC 9110
   (401 versus 403).
7. Write one horizontal example (same role, other user's object) and one
   vertical example (role that must not reach an admin or privileged
   action) from this system. Update the threat-model register.

## Required evidence

- A findings note listing at least 2 authorization defects with route,
  object identifier, and the two local users used to demonstrate them
- Git history showing each fix in its own commit
- A committed test in which user A cannot read, update, or delete user
  B's object through the documented object-id route
- Captured HTTP for unauthenticated, authenticated-but-unauthorized, and
  authorized requests to the same route
- Notes that name one horizontal and one vertical privilege example from
  this system
- Reflection note answering the task questions

Where code is produced, submit a repository URL plus an immutable commit
or tag reference. Do not submit only screenshots of code.

## Acceptance criteria

- [ ] An authenticated user cannot read, update, or delete another user's
      object through the documented object-id route; a committed test
      shows 401 or 403, and the notes state which.
- [ ] An unauthenticated request to a protected route receives 401; an
      authenticated but unauthorized request receives 403, or the notes
      document and justify a different pair.
- [ ] At least one function-level check is enforced server-side on a
      privileged action, not only hidden in the user interface.
- [ ] At least 2 authorization defects found in the owned or local app
      are listed with route or file location and shown fixed.
- [ ] The notes name one horizontal and one vertical privilege example
      taken from this system.

The mentor may hand you a third object id live and ask what the server
must check before loading it. A UI-only restriction is not enough.

## Reflection

Answer these in your own words after doing the work:

1. What is the difference between an authentication bug and an
   authorization bug, using one example from this app for each?
2. Why is "return 404 for another user's object" a product choice rather
   than a substitute for an authorization check?
3. Which check is object-level and which is function-level in your
   privileged action?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to distinguish authentication failure from
  authorization failure using the three captured responses.
- Give a new object id and ask which server-side check must run before
  the handler reads the store.
- Do not approve a submission whose only control is a hidden route in
  the client.

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
