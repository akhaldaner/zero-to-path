# Templates

Universal English templates for an evidence-based self-study system.

These templates are intentionally generic. Replace placeholders in double braces before use.

## Core model

The system separates four objects:

| Object                | Role                                                                                               |
| --------------------- | -------------------------------------------------------------------------------------------------- |
| Knowledge map         | Source of truth for topic status                                                                   |
| Study note / artifact | Carrier of material and independent work                                                           |
| Daily log             | Single regular form filled by the learner                                                          |
| Dispatcher state      | AI-generated handover snapshot, not a status registry                                              |
| Master config         | Is the normative template for the whole system; the remaining templates are its operational forms. |

The learner does not maintain status inside notes. Status lives only in the knowledge map.

## Statuses

| Status | Meaning |
|---|---|
| `in_progress` | Active work is happening, but the topic is not yet verified |
| `unverified` | An artifact exists, but confirmation has not passed or evidence is insufficient |
| `mastered` | The subject mentor submitted a petition, and the dispatcher confirmed the topic into the knowledge map |

There is no `not_started` status inside active maps. Unopened topics remain in the source backlog.

## Artifact types

| Type | Meaning |
|---|---|
| `NOTE` | Concept note, theory, explanation. A note alone does not produce mastery |
| `DRL` | Drill, practicum, task or group of tasks |
| `UNT` | Learning unit, especially for practical subjects |
| `ADR` | Architecture or project decision record |
| `EXM` | Exam or transition check |

Tests are not separate artifact types. They live inside `DRL`, `UNT`, or `EXM`.

## Artifact ID format

```text
{{SUBJ}}-{{TYPE}}-{{NN}}-{{slug}}
```

Rules:

- `{{SUBJ}}` is a short subject code, for example `MATH`, `PROG`, `LANG`, `SYS`, `CS`, `PROJ`.
- `{{TYPE}}` is one of `NOTE`, `DRL`, `UNT`, `ADR`, `EXM`.
- `{{NN}}` is a two-digit number from `01` to `99`.
- `{{slug}}` is lowercase kebab-case, 2–5 words.
- The filename equals the artifact ID plus `.md`.
- The artifact ID is immutable.
- Numbers are not reused after deletion.

## Minimal workflow

1. Create or update the knowledge map for the subject.
2. Create an artifact file using the appropriate template.
3. Do the work independently.
4. The subject mentor verifies independence, test/tasks, written answers, verification, and error analysis.
5. If criteria are met, the mentor generates a petition.
6. The learner inserts the petition into the daily log.
7. The dispatcher validates the petition and generates map rows plus dispatcher state.
8. The learner inserts map rows into the knowledge map and dispatcher state into the local dispatcher file.

## Operating rules

- Knowledge maps are the source of truth.
- Notes do not store status.
- A `NOTE` alone never produces `mastered`.
- Only `DRL`, `UNT`, or `EXM` can produce a petition.
- Written answers to the mentor are mandatory.
- Oral practice may be used as personal reinforcement, but it is not a system gate.
- A new topic does not open until the active debt in the same subject is closed.
- AI-generated tasks are allowed only when they are correct, verifiable, appropriate to the current level, and marked as AI variants.
- The original source remains the arbiter.
- The learner fills only the daily log manually. Mentors and dispatchers generate petitions, responses, and handover state.

## File map

| Template              | Use                                                                                              |
| --------------------- | ------------------------------------------------------------------------------------------------ |
| `knowledge_map.md`    | Subject-level source of truth                                                                    |
| `study_note.md`       | Universal artifact skeleton                                                                      |
| `daily_log.md`        | Single daily learner form                                                                        |
| `dispatcher_state.md` | AI-generated handover snapshot                                                                   |
| `petition.md`         | Formal mastery request from subject mentor                                                       |
| `adr.md`              | Project or architecture decision record                                                          |
| `exam.md`             | Mini-exam or transition check                                                                    |
| `practical_unit.md`   | Lab, command-line, language, or applied practice unit                                            |
| `ai_role_prompts.md`  | Starter prompts for mentor and dispatcher chats                                                  |
| `master_config.md`    | Normative system template; other files are operational forms                                     |