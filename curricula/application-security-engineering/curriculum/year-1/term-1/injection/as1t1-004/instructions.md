# Injection: Find, Fix, Prove

**Task ID:** `as1t1-004`  
**Estimated effort:** 10 hours  
**Module:** Injection

## Why this task exists

The reference software-engineering web-security task asks for notes on
injection and a toy fix. This task requires two real sinks in *your*
application, a control that is not string concatenation, and a test that
goes red when the old concat is restored. The red-then-green cycle is
the proof.

This is an apprenticeship task, not a reading checkbox. Completion requires
evidence that you can apply and explain the ideas.

## Scope rule

Work only on an application you own or a local lab you start and stop
yourself. Craft inputs only against that local process. Do not send
injection payloads to any third-party host.

## Authoritative resources

- **OWASP Top 10** (primary): https://owasp.org/www-project-top-ten/

PortSwigger SQL injection and command-injection *articles* may be used
as free reading. Do not run hosted labs or target third-party systems.

## Work to complete

1. Search the owned or local app for sinks where request data, file
   names, or stored fields are concatenated into SQL, ORM raw queries,
   shell commands, or server-side templates. Record file and line or the
   query-builder call.
2. Identify at least two distinct sinks. Prefer two classes (for example
   SQL and command, or SQL and template) if both exist; two SQL sinks
   in different handlers are acceptable if the app has no second class.
   If the app has none, seed two temporary local sinks on a branch,
   document them, then fix them.
3. For each sink, write the unsafe construction, the intended control
   (parameterized query, allow-list of flags, compiled template with
   auto-escape, etc.), and the OWASP category.
4. Fix each sink so user input is not concatenated into the statement or
   command string. Put each fix in its own commit.
5. Write a committed test for at least one sink that fails when you
   restore the concatenation and passes with the fix. Record the command
   and both outputs. Restoring concat must be done on a disposable
   branch or a revert you then undo — do not leave the vulnerable
   construction on the submitted default branch.
6. Update the threat-model register for the injection threats you closed.

## Required evidence

- A findings note listing at least 2 injection sinks with file and line
  or query-builder call, the injection class, and the OWASP category
- Git history showing each sink fixed in its own commit
- A committed test that fails when concatenation is restored on at least
  one sink and passes with the fix in place, with command and output
  recorded
- The fixed query or command construction in source, with no user input
  interpolated into the statement string
- Reflection note answering the task questions

Where code is produced, submit a repository URL plus an immutable commit
or tag reference. Do not submit only screenshots of code.

## Acceptance criteria

- [ ] At least 2 distinct injection sinks are identified with file and
      line or query-builder call in the owned or local app.
- [ ] Each identified sink is changed so user input is not concatenated
      into a query string, command string, or template expression.
- [ ] For at least 1 sink, a committed test fails when the concatenation
      is restored and passes with the fix in place; command and both
      outputs are recorded.
- [ ] The notes map each sink to an OWASP Top 10 category and name the
      control used (parameterized query, allow-list, or equivalent).

The mentor may restore the old concat on a scratch branch and ask you
to run the test. A claim that "we use an ORM" without a located sink is
not enough.

## Reflection

Answer these in your own words after doing the work:

1. Why does input validation alone not replace a parameterized query?
2. What did the failing test actually observe — an error, unexpected
   rows, or a shell side effect — and why was that the right signal?
3. Which of your two sinks was easier to miss in review, and why?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Restore concatenation on a scratch branch and ask the apprentice to
  run the proving test.
- Ask where an ORM still exposes a raw-SQL or annotation escape hatch
  in this stack.
- Do not approve notes that only restate "use prepared statements"
  without file locations.

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
