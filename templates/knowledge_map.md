# {{Subject}} — Knowledge Map

## 1. Source

- Active source: {{source}}
- Current focus: {{current_focus}}
- Reference / archive: {{reference_archive}}
- Source change trigger: checklist = `mastered` + 2 mini-exams PASS; confirmed by dispatcher.

## 2. Topic checklist

| artifact_id | Topic | Level | Status | Proposed | Confirmed | Evidence |
|---|---|---|---|---|---|---|

## 3. Key rules

- Working status chain: `in_progress` → `unverified` → `mastered`.
- The subject chat does not set `mastered`; it only submits a `PETITION`.
- `mastered` is valid only after dispatcher confirmation; date and evidence are required.
- Filename = `artifact_id.md`; a map row without a file and a file without a map row are defects.
- `artifact_id` is immutable; `NN` is chosen by the learner, AI asks when needed.
- A debt is closed in the next block of the same subject; a new topic does not open before the debt is closed.
- Legacy files without `artifact_id` are not defects until they are taken into migration.
- Written answers to the mentor are mandatory.
- `NOTE` alone does not produce `mastered`.
- `DRL`, `UNT`, and `EXM` may end with `PETITION`.

## 4. Sorting

1. `in_progress`
2. `unverified`
3. `mastered`

## 5. Glossary

| Term / index | Meaning |
|---|---|
| `artifact_id` | `{{SUBJ}}-{{TYPE}}-{{NN}}-{{slug}}` |
| `SUBJ` | Subject code, for example `MATH`, `PROG`, `LANG`, `SYS`, `CS`, `PROJ` |
| `TYPE` | `NOTE`, `DRL`, `UNT`, `ADR`, `EXM` |
| `NN` | `01`–`99`, not reused |
| `slug` | lowercase kebab-case, 2–5 words |
| `in_progress` | Work is active |
| `unverified` | Artifact exists, confirmation not passed |
| `mastered` | Confirmed by dispatcher |
| `L1`–`L6` | Optional level scale; use `—` when not applicable |
| `PETITION` | Subject chat request to mark a topic as `mastered` |

## 6. Change log

| Date | Change | Basis |
|---|---|---|