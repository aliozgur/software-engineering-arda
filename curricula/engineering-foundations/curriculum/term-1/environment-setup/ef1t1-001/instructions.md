# Set Up a Professional Development Environment

**Task ID:** `ef1t1-001`
**Estimated effort:** 4 hours
**Module:** Environment Setup

## Why this task matters

You will spend the next several months doing almost everything in this curriculum from a terminal and an editor. If your environment is a pile of half-remembered installs, every later task gets slower and harder to reproduce. This task asks you to build that environment deliberately once, write down exactly how you built it, and prove the notes are enough to rebuild it — because that is exactly what will happen the next time you get a new machine.

## Authoritative resource

- **MIT — The Missing Semester of Your CS Education**: https://missing.csail.mit.edu/2026/

Use its shell and tooling material as your primary reference. You may use other sources, but record them in your notes and prefer official documentation over random blog posts.

## What you'll do

1. Install (or confirm you already have) a Unix-like shell, Git, Python 3, and a code editor you can drive from the keyboard.
2. Set your Git identity (`user.name`, `user.email`) and check it with `git config --list`.
3. Create a setup-notes repository. As you go, commit your notes in stages — not as one final write-up.
4. For every tool installed, write down the exact command used and one sentence on why you need it.
5. Practice at least 10 different shell operations and record the commands and their output: navigating directories, piping/redirecting output, listing and setting an environment variable, checking file permissions, and inspecting a running process (e.g. with `ps` or Task Manager equivalent).
6. Close your terminal, open a brand-new one, and re-run your documented steps from scratch. Fix your notes until this actually works without you filling in a gap from memory.

## Evidence to submit

- A Git repository containing setup notes, with more than one commit showing the notes were built up over time, not written after the fact.
- The setup notes file itself, naming each tool, the exact install command, and one line on why it's needed.
- A terminal transcript or log showing at least 10 distinct shell commands run, with their output.
- An AI disclosure entry if AI helped write or debug any part of the setup.

## Acceptance criteria

- [ ] A setup notes file lists every tool installed and the exact command or steps used to install it.
- [ ] Following the documented steps from a brand-new terminal session reproduces a working `git`, `python3`, and editor invocation with no undocumented steps.
- [ ] At least 10 distinct shell commands are used and explained in the notes, covering navigation, redirection, environment variables, permissions, or process inspection.
- [ ] No API key, token, or password appears in any committed file.

Check your own submission against each line above before asking for review — a mentor will check the same four things.

## Reflection

Answer briefly, in your own words:

1. Which step would have failed if you'd relied on memory instead of your notes?
2. What is still specific to your machine, and what would you have to change to run this on a teammate's machine?

## Mentor review guide

- Follow the apprentice's notes from a brand-new terminal session. Do not approve if a step they needed from memory is missing from the notes.
- Open the repository history. One final commit of polished notes is not enough.
- Scan committed files for secrets. A leaked token is an automatic revision request.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI assistance for this task

Mode: **guided**. You can ask for explanations, hints, or quiz yourself on shell/Git concepts. This task does not allow AI to generate your setup notes or install steps for you — the point is that you did the setup and can explain every line of your own notes. Disclose any AI use in your submission notes: what you asked, and what you verified yourself afterward.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and a mentor — or a documented self-check against every acceptance criterion, if you are working without one — confirms the demonstrated competency.
