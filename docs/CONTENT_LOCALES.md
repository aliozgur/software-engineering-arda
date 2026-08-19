# Content locales

Canonical curriculum files stay in the **source locale** (default English). Translations are **sibling overlays**. Do not copy `curriculum/` into `en/` and `tr/` trees — that would duplicate task ids and break learner/mentor overlays.

## Manifest

On each `curriculum.json` (do **not** reuse `languages` — that field is programming languages):

```json
"sourceLocale": "en",
"contentLocales": ["en", "tr"]
```

Both optional. Missing `sourceLocale` means `en`.

## Sibling files

Locale is a language code (`tr`), not `tr-TR`.

| Canonical | Overlay |
|---|---|
| `curriculum.json` | `curriculum.tr.json` |
| `term.json` | `term.tr.json` |
| `task.json` | `task.tr.json` |
| `instructions.md` | `instructions.tr.md` |
| `competencies/{id}.json` | `competencies/{id}.tr.json` |
| `resources/{id}.json` | `resources/{id}.tr.json` |

Overlay JSON is **sparse**: only translatable keys. It must not change `id`, paths, `aiPolicy`, hours, or competency/resource ids. See [locale-overlay.schema.json](../schemas/locale-overlay.schema.json).

The app merges field-by-field: overlay value present and non-empty wins; otherwise the canonical file. Missing overlay files are not an error.

## Shared libraries

`competencies/` and `resources/` live **once at the repository root**. Nested `curricula/<slug>/competencies/` or `resources/` is an optional override of the same id, not a second library.

## Personal overlays

Do not translate `learners/` or `mentors/`. Those stay as the author wrote them.
