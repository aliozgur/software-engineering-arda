# Land a Small Change in Someone Else's Code

**Task ID:** `ef1t2-004`
**Estimated effort:** 8 hours
**Module:** Feature Work

## Why this task matters

On the job you will spend most weeks changing code you did not write, in a style you did not choose. The amateur move is to add a new helper, a new naming scheme, and a new test layout because that is how *you* would have started the project. The professional move is to find how this codebase already does the same kind of thing, make the smallest change that fits, and leave tests a reviewer can run.

## Authoritative resources

- **Harvard CS50P — Introduction to Programming with Python** (primary): https://cs50.harvard.edu/python/
- **Python 3 Tutorial** (reference): https://docs.python.org/3/tutorial/
- **MIT — The Missing Semester of Your CS Education** (reference): https://missing.csail.mit.edu/2026/

Use search tools from Missing Semester to find the existing pattern. Use CS50P and the Python docs for the language you are changing — not to relearn Python, but to match the code that is already there.

## What you'll do

1. Use a Python codebase you did not write. Prefer the one you mapped in `ef1t1-003`. It must already have more than one module and some existing tests or an obvious place tests would go.
2. Pick a change that is real and small: a bug fix, a documented missing behavior, or a narrow improvement. If you cannot name the change in one sentence, it is too big.
3. **Before you write production code**, commit a design note that names: the files you expect to touch, one existing pattern you will follow (with a file path if you already found it), how you will verify the change, and what is out of scope.
4. Implement the change. Production code may touch at most three existing files. Tests may add files. Follow the existing naming, error handling, and test layout — do not introduce a second style.
5. Add at least two automated tests for the new or changed path. Run them with a single documented command.
6. Open a pull request whose description states the problem first, then the change, then the verification command, then what you left out.
7. In a convention note, quote two existing conventions with `file:line` and point at the matching `file:line` in your change.

## Evidence to submit

- A design-note commit whose position in `git log` comes before any implementation commit.
- The production-code diff, limited to the scoped files named in the design note.
- Test-command output showing at least 2 new test cases for the new or changed behavior, all passing.
- A pull request link plus the description text (problem, change, verification, out of scope).
- A convention note citing at least 2 existing patterns with file and line, and the matching location in your change.
- An AI disclosure entry if AI helped choose the approach or write the change.

## Acceptance criteria

- [ ] A design-note commit exists before any implementation commit and names the files you planned to touch, the existing pattern you planned to follow, and how you planned to verify the change.
- [ ] The production-code diff touches at most 3 existing files, not counting new or existing test files.
- [ ] At least 2 new automated test cases cover the new or changed behavior, and the documented test command shows them passing.
- [ ] The convention note cites at least 2 existing patterns with file path and line number, and names the file and line in your change that follows each one.

Check your own submission against each line above before asking for review — a mentor will check the same four things.

## Reflection

Answer these in your own words after doing the work:

1. Which existing convention were you tempted to "improve," and what would a reviewer have had to learn if you had?
2. What did you cut from the first version of the change to stay inside three production files?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you followed the codebase you found, not a style you invented?

## Mentor review guide

- Check `git log` order. A design note committed after the implementation is a revision.
- Count production files in the diff. A fourth existing production file is a revision unless they split the work and resubmit a smaller change.
- Open the two cited conventions and the matching new lines. If the citation is a README claim with no code line, request revision.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI assistance for this task

Mode: **guided**. Explanations of an unfamiliar pattern you already located are allowed. Asking AI to choose the change, invent the design, or write the patch is not — the map and the convention citations have to come from code you opened. Disclose any AI use: what you asked, and what you verified in the files yourself.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and a mentor — or a documented self-check against every acceptance criterion, if you are working without one — confirms the demonstrated competency.
