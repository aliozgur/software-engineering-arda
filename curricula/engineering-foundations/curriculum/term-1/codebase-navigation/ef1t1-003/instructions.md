# Map an Unfamiliar Codebase

**Task ID:** `ef1t1-003`
**Estimated effort:** 6 hours
**Module:** Codebase Navigation

## Why this task matters

On the job, you will rarely start from an empty file. You will start from someone else's code, usually with no one available to walk you through it. The professional skill is not memorizing every codebase you touch — it's having a repeatable method to orient yourself quickly using the tools already on your machine.

## Authoritative resource

- **MIT — The Missing Semester of Your CS Education** (primary): https://missing.csail.mit.edu/2026/

## What you'll do

1. Choose a codebase you did not write: a real open-source Python project of at least a few hundred lines across multiple files, or one your mentor assigns.
2. Find its entry point — the file or function that actually runs first — using search tools (`grep`/`ripgrep`, `find`, your editor's project search), not by guessing from the folder names.
3. List its top-level modules or directories, and write one line on what each is actually for, based on opening the files, not just reading the README.
4. Pick one module and go deeper: list its public functions or classes, find at least one place that calls into it, and at least one thing it depends on.
5. As you go, keep a running log of the actual commands you use to find each answer.

## Evidence to submit

- The written map (a Markdown file), committed to a notes repository.
- A terminal transcript showing at least 5 of the actual search commands you ran, with enough surrounding output to show what they found.
- An AI disclosure entry if AI was used to help interpret any part of the code.

## Acceptance criteria

- [ ] The written map names the codebase's entry point and how it was located.
- [ ] The map lists at least 5 top-level modules or directories with a one-line description of each, based on reading the code, not the README alone.
- [ ] One module is described in depth: its public functions or classes, and at least one caller and one dependency, each named specifically.
- [ ] The map states which search commands were used to find each piece of information.

## Reflection

1. What did the README get wrong or leave out compared to what you found by reading the code?
2. Which search command turned out to be the most useful, and why?

## Mentor review guide

- Compare the written map to the transcript. Every claimed entry point or module should have a search command that found it.
- Ask the apprentice to open the named caller and dependency live. If they cannot find those names in the code, request revision.
- Do not approve a map that only restates the project's README.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI assistance for this task

Mode: **guided**. You may ask an AI assistant to explain an unfamiliar language construct or pattern once you've found it yourself. Asking AI to summarize or map the codebase for you defeats the purpose — the map must reflect what you actually located and read.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and a mentor — or a documented self-check against every acceptance criterion, if you are working without one — confirms the demonstrated competency.
