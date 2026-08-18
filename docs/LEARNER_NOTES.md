# Learner notes

Notes are **fork-owned**, not curriculum. The upstream repository only defines the contract. A learner/mentor fork writes the files.

## Layout

```text
learners/<learner-id>/tasks/<task-id>/
  state.json
  reflection.md
  evidence.md
  worklog.json
  notes/
    <note-id>.json
    <note-id>.md
```

| File | Role |
|---|---|
| `reflection.md` | Durable reflection (explicit save, not keystroke autosave) |
| `evidence.md` | Evidence note used at submit |
| `state.json` | Task status + `aiDisclosure` (`none` / `assisted` / `generated`) |
| `worklog.json` | Time entries (`1h`, `30m`, `1h 30m`); `minutes` is the durable value |
| `notes/<id>.json` | Note metadata and optional instruction quote |
| `notes/<id>.md` | Note body (Markdown) |

Do not put notes under `curriculum/`. That tree is curator-owned.

If you share the fork as a new curriculum, remove `learners/` and `mentors/` from the copy you publish. See [GIT_FORK_MODEL.md](GIT_FORK_MODEL.md).

## Time log

`worklog.json` is a list of explicit time entries. The apprentice types `1h`, `30m`, or `1h 30m` (hours and minutes only, optional space, optional decimal hours like `1.5h`). The app stores both the original `input` and integer `minutes` (max 24h per entry). Time logs are not required to submit.

## Fragment anchors

A note may quote a passage from `instructions.md`:

```json
{
  "schemaVersion": 1,
  "id": "a1b2c3",
  "taskId": "y1t1-002",
  "title": "Working tree vs index",
  "createdAt": "2026-08-18T13:00:00Z",
  "updatedAt": "2026-08-18T13:00:00Z",
  "anchor": {
    "source": "instructions",
    "quote": "the working tree is your sandbox"
  }
}
```

`quote` is the selected text. The app matches it as a substring of the instructions Markdown. Offsets are not stored so a later curriculum wording change degrades to an unanchored note instead of a broken index.

## Markdown links

Inside `notes/<id>.md`:

| Write | Meaning |
|---|---|
| `[[note:<note-id>]]` | Another note on the same task |
| `[[task:<task-id>]]` | A curriculum task |
| `[label](https://…)` | Ordinary Markdown link |

The app expands wiki links to `apprenti://note/…` and `apprenti://task/…` when rendering.

## AI disclosure

When `task.json` has `aiPolicy.disclosureRequired: true`, submit requires an explicit `aiDisclosure` on `state.json`. Empty is not “none”. See the in-app help topic “What is AI disclosure?”.
