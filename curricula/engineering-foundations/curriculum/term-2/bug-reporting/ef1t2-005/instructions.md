# Write a Bug Report Someone Else Can Reproduce

**Task ID:** `ef1t2-005`
**Estimated effort:** 5 hours
**Module:** Bug Reporting

## Why this task matters

A ticket that says "login is broken" or "the script fails sometimes" costs the next person an investigation you already did and forgot to write down. A report they can reproduce without asking you is professional communication: environment, steps, expected versus actual, and the smallest input that still fails. This task stops at the report. The fix is a different change.

## Authoritative resources

- **Harvard CS50P — Introduction to Programming with Python** (primary): https://cs50.harvard.edu/python/
- **Python 3 Tutorial** (reference): https://docs.python.org/3/tutorial/

Use them when you need to write a small failing script or test in Python. The quality bar is the report, not a clever patch.

## What you'll do

1. Find or create a real, reproducible defect in Python code. Good sources: a leftover surprise from `ef1t1-004`, a bug you hit in `ef1t1-005` before you fixed it (reintroduce it on a disposable branch), or a small open issue on a project you can run locally. "The code looks ugly" is not a defect for this task.
2. Reduce it to a minimal failing input or script. If reproduction still needs more than a short command plus that input, keep cutting.
3. Write a Markdown report with every one of these headings: **Title**, **Environment** (OS, Python version, relevant package versions), **Steps** (numbered), **Expected result**, **Actual result**, **Minimal input or script**, **What I already tried**. Do not include a proposed patch. Do not state a root cause as fact; a suspicion can live under "What I already tried."
4. Hand the report — not the surrounding investigation notes — to someone who has not seen the code. If no one is available, wait at least a few hours, open a new terminal, and follow only the report. Record whether it reproduced on the first try.
5. If the second attempt failed, add the missing sentence to the report and record the exact sentence you added.
6. Commit a failing automated test or script whose output matches the report's **Actual result** sentence. Do not fix the defect in this task.

## Evidence to submit

- The bug-report Markdown file containing environment, numbered steps, expected result, actual result, and a minimal input or script.
- A reproduction log from a second attempt (another person, or you after at least a few hours in a new terminal) that used only the report.
- Output of a failing automated test or script whose printed or asserted actual result matches the report's actual-result sentence.
- An AI disclosure entry if AI helped draft the report or the failing case.

## Acceptance criteria

- [ ] The report file contains all of: environment (OS, Python version, relevant package versions), numbered reproduction steps, expected result, actual result, and a minimal input or script.
- [ ] A second reproduction attempt is documented as succeeding from the report alone, or the log quotes the exact sentence that had to be added before it succeeded.
- [ ] A committed failing test or script produces output that matches the report's actual-result sentence.
- [ ] The report does not include a proposed patch or a root-cause claim presented as fact — this task is the report, not the fix.

Check your own submission against each line above before asking for review — a mentor will check the same four things.

## Reflection

Answer these in your own words after doing the work:

1. Which sentence in the first draft would have made a teammate bounce the ticket, and what did you replace it with?
2. What did you have to cut from the failing case to make it minimal, and what broke when you cut too far?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves a stranger could reproduce the defect without asking you?

## Mentor review guide

- Cover everything except the report and try the steps. If you need a missing version, path, or input, request revision.
- Compare the failing test/script output to the actual-result sentence. They must match; a vague "it failed" in the report is a revision.
- If the report includes a patch or a confident root cause, ask them to delete it and resubmit. The next task is not this one.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI assistance for this task

Mode: **guided**. Hints on how to structure a report or how to write a failing `pytest` case are allowed. Generating the report from a stack trace you have not reduced, or inventing steps you did not run, is not. Disclose any AI use: what you asked, and which steps you re-ran yourself.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and a mentor — or a documented self-check against every acceptance criterion, if you are working without one — confirms the demonstrated competency.
