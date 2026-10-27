---
document: MASTER_CONFIG_TEMPLATE
title: "MASTER CONFIG: {{learner_name}} ({{edition_name}})"
version: "{{version}}"
status: active
learner: "{{learner_name}} ({{learner_age}})"
mentor_mode: active
updated: {{date}}
changelog: "{{changelog}}"
---

# MASTER CONFIG: {{learner_name}} ({{edition_name}})

---

## 0. Document passport and markup system

### 0.1. Purpose

This section is the meta-level of the config. It defines how the document itself and all derived artifacts (notes, knowledge maps, drills, units, exams, daily logs, dispatcher state) are structured. The goal is to make the knowledge base machine-readable, navigable, and resistant to Markdown breakage during copying. Any formatting rule scattered across the body is consolidated here into a single convention; the body must follow it.

### 0.2. Heading hierarchy

The document uses up to `H5`.

| Level | Syntax | Meaning | ID format |
|---|---|---|---|
| H1 | `#` | Document title. Exactly one per file. | — |
| H2 | `##` | Top-level section. | `## N. NAME` |
| H3 | `###` | Subsection. | `### N.M NAME` |
| H4 | `####` | Sub-subsection / protocol item. | `#### N.M.K NAME` |
| H5 | `#####` | Standard item inside a protocol. | `##### N.M.K.P NAME` |

Rules:

- Every `H2`–`H5` starts with a numeric ID.
- Service headings without a number: `## Contents`, `## Appendix ...`.
- One blank line before every heading.
- Internal references use `§ID`.

### 0.3. Identifier and link format

A config block address is its numeric ID with the `§` prefix: `§4.3`, `§5.2.4`, `§7`.

A link from a vault note to a map or artifact uses a wiki-link, for example `[[{{subject}}_map_of_content]]`, `[[{{SUBJ}}-{{TYPE}}-{{NN}}-{{slug}}]]`.

Referencing a block by title alone is forbidden when the title may change on revision.

### 0.4. Frontmatter and index headers

`YAML-frontmatter` is mandatory only for `MASTER_CONFIG`.

Knowledge maps and study notes do not use YAML-frontmatter.

Study notes use a minimal index header:

```text
# {{artifact_id}} — {{topic_title}}

source: {{source}}
date: {{date}}
```

Status is not stored inside the note file. Status lives only in the knowledge map.

### 0.5. Fence and copying convention

- Internal code fences in the document use exactly three backticks.
- When the whole config is transferred as one block, the outer transport fence must exceed the innermost fence.
- Templates containing code fences are given as live Markdown or as `text` fences, never as code-inside-code at the same depth.
- Unclosed fences, broken table rows, stray characters, and internal AI remarks inside a copied block are forbidden.

### 0.6. Table convention

- Every table has a header row and a separator row.
- Cell count per row matches the column count.
- A literal pipe inside a cell is escaped as `\|`.
- Prefer words over raw pipe symbols where possible.

### 0.7. List and semantic marker convention

- Uniform markers within one list.
- Nested lists indent by exactly two spaces.
- Semantic markers:
  - ⚠️ error / risk;
  - 💡 insight / heuristic;
  - ✅ check / criterion;
  - 🧪 experiment / deliberate break;
  - ♻️ repetition;
  - 📋 report.

Markers do not replace heading structure.

### 0.8. Broken-block repair rule

If the learner reports that a block is broken, torn, not copyable, or has invalid syntax, the AI must:

- not patch fragmentarily;
- not send only a piece;
- regenerate the whole block;
- preserve the full structure;
- eliminate the Markdown cause;
- return one intact block.

### 0.9. Markup validity checklist

Before emitting any block, the AI verifies:

- exactly one `H1`;
- all `H2`–`H5` carry numeric IDs except service headings;
- blank lines precede headings;
- tables have correct separators;
- bare pipes in table cells are escaped;
- internal fences are closed;
- no broken words or stray characters;
- no internal AI remarks inside a copied block;
- config references use `§ID`.

---

## 1. Philosophy and strategic vision

### 1.1. Architect, not user

The learner is not memorizing syntax. The learner is building understanding that connects high-level services to the physical layer of the system.

The goal is engineering thinking capable of reasoning about:

- code;
- system;
- data;
- algorithms;
- mathematics;
- infrastructure;
- product.

### 1.2. Shaped expertise

The learner defines one deep vertical track and one broad horizontal layer.

```text
Vertical: {{primary_track}}
Horizontal: {{secondary_tracks}}
```

Both are built in parallel over years until they meet where the primary track touches the underlying layer.

### 1.3. Order matters

Discipline says: secure the in-demand primary track first, then descend into secondary layers.

Mixing layers too early is how learners stall. Order is strategy, not preference.

```text
Primary track: {{track_1}} — market and resources.
Secondary track: {{track_2}} — depth, entered from stability.
Tertiary track: {{track_3}} — hardest layer, entered last.
```

### 1.4. Balance, not sprinting

Every subject moves every week. Subjects feed each other:

```text
{{subject_a}} feeds {{subject_b}};
{{subject_b}} explains {{subject_c}};
{{subject_d}} makes the machine tangible;
{{subject_e}} accelerates access;
{{project}} integrates skills into a product.
```

Forbidden imbalances:

- a week of only one subject;
- an abandoned subject;
- a project replacing foundations;
- a new unit opened before an active debt is closed.

### 1.5. Repetition beats volume

Knowledge that cannot be recalled does not exist for the engineer.

Every topic passes through practicum:

- independent work;
- test or tasks;
- written answers to the mentor;
- verification of result;
- error analysis.

Without practicum a topic is not considered learned.

### 1.6. Evidence-based progress

`mastered` is not a feeling. It is a procedural state:

- an artifact exists;
- the subject chat verified the work;
- the subject chat submitted a `PETITION`;
- the dispatcher confirmed;
- the knowledge map received a row with date and evidence.

Knowledge maps are the source of truth.

`Dispatcher_state` is an operational snapshot, not a status registry.

### 1.7. Low bureaucracy

The system must not consume study time.

The learner fills a minimum:

- `daily_log`;
- pastes ready blocks generated by AI.

Mentors and dispatchers do the verification work behind the scenes.

### 1.8. Document hygiene as engineering norm

Markdown validity, links to maps, uniform templates are part of discipline.

A broken or structureless note degrades the second memory the way a bug degrades code.

---

## 2. Multi-phase roadmap

| Phase | Period | Goal | Stack | Status |
|---|---|---|---|---|
| {{phase_0}} | {{period_0}} | {{goal_0}} | {{stack_0}} | Active |
| {{phase_1}} | {{period_1}} | {{goal_1}} | {{stack_1}} | Pending |
| {{phase_2}} | {{period_2}} | {{goal_2}} | {{stack_2}} | Pending |
| {{phase_3}} | {{period_3}} | {{goal_3}} | {{stack_3}} | Pending |

Phases are passed by readiness criteria, not by calendar.

---

## 3. Toolchain and active sources

### 3.1. Base stack

- OS: {{os}}
- Editor: {{editor}}
- Knowledge base: {{knowledge_base}} (vault: `{{vault_name}}/`)
- Version control: {{vcs}} (`{{vcs_user}}`) + {{remote}} (`{{repo_url}}`)
- Project repository: {{project_repo}} ({{project_visibility}})
- Backup: {{backup_method}} ({{backup_schedule}})

Central nodes are knowledge maps `{{subject}}_map_of_content.md` per subject (mandatory template — §4.2). Notes in `Notes/` must link to maps via wiki-links. `Resources/` folders are file storage, NOT a curriculum. Note, map, and scenario templates — §4, §5. Markup of all artifacts — §0.

### 3.2. Active sources

| Subject | Active source | Role |
|---|---|---|
| {{subject_1}} | {{source_1}} | {{role_1}} |
| {{subject_2}} | {{source_2}} | {{role_2}} |
| {{subject_3}} | {{source_3}} | {{role_3}} |
| {{subject_4}} | {{source_4}} | {{role_4}} |
| {{subject_5}} | {{source_5}} | {{role_5}} |
| {{project}} | {{project_spec}} and roadmap in repo | Applied polygon |

### 3.3. One active source rule

At any moment one primary source per subject, or a coherent pair (textbook + problem book). The rest is reference, archive, deepening.

Source change is recorded in the knowledge map and confirmed by the dispatcher.

### 3.4. Source change trigger

A source is exhausted when:

- the map checklist is fully `mastered`;
- at least two mini-exams on its topics passed with verdict `PASS`.

### 3.5. Fallback when source unavailable

If the active source is temporarily unavailable:

- the AI mentor gives tasks of the same class as in the source;
- this is not a source change;
- the textbook and notes remain the arbiter;
- after the source is restored, a reconciliation is run;
- on divergence, a `mastered` status may be revoked;
- fallback does not last longer than two consecutive weeks without review.

---

## 4. Vault structure and knowledge-base standards

### 4.1. Target tree

The current tree is used without mass restructuring. Only knowledge maps, the operational dispatcher file, and folders for new artifacts are added as needed.

```text
{{vault_name}}/
├── {{subject_1}}/
│   ├── {{subject_1}}_map_of_content.md
│   ├── Notes/
│   ├── Tests/ or Tasks/
│   └── Resources/
├── {{subject_2}}/
│   ├── {{subject_2}}_map_of_content.md
│   ├── Notes/
│   ├── Tests/
│   ├── Resources/
│   └── Projects/
│       └── {{project}}/
├── {{subject_3}}/
│   ├── {{subject_3}}_map_of_content.md
│   ├── Notes/
│   ├── Tests/
│   └── Resources/
├── {{subject_4}}/
│   ├── {{subject_4}}_map_of_content.md
│   ├── Notes/
│   ├── Tests/
│   └── Resources/
├── {{subject_5}}/
│   ├── {{subject_5}}_map_of_content.md
│   ├── Notes/
│   ├── Tests/
│   └── Resources/
├── Daily/
│   ├── Dispatcher_state.md
│   ├── Logs/
│   └── Templates/
│       ├── daily_log.md
│       └── study_note.md
├── {{vcs}}/
│   └── {{repo}}/
│       ├── code/
│       ├── docs/
│       └── templates/
└── Inbox/
```

Notes:

- `Tests/` or `Tasks/` is created at the first practical artifact of the subject.
- The project has no knowledge map in the vault; its roadmap lives in the repository.
- Legacy folders may remain; new artifacts follow the standard placement in §4.4.

### 4.2. Knowledge map template

Knowledge maps are the source of truth for topic status.

Maps have no YAML-frontmatter.

```text
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
- Legacy files without `artifact_id` are not defects until taken into migration.
- Written answers to the mentor are mandatory.
- `NOTE` alone does not produce `mastered`.
- `DRL`, `UNT`, `EXM` may end with `PETITION`.

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
```

Map rules:

- `NOTE` alone never produces `mastered`.
- `DRL`, `UNT`, `EXM` may produce `PETITION`.
- The `Evidence` column is filled by the dispatcher, usually as a link to the artifact plus a petition-accepted mark.
- The learner does not fill the evidence column manually.

### 4.3. Note index header

Every study artifact begins with a minimal index header.

```text
# {{artifact_id}} — {{topic_title}}

source: {{textbook / course / task / specification}}
date: {{YYYY-MM-DD}}
```

Rules:

- Filename equals `artifact_id.md`.
- The file does not repeat `subject`, `type`, `status`, `related`, `artifact_id` when these are already clear from the name and the map.
- `source` is mandatory for `DRL`, `UNT`, `EXM`.
- For `NOTE` and `ADR`, `source` is desirable; if the source is internal, write `internal` or the specification name.
- `date` is the creation or migration-start date, not the confirmation date.
- The link to the map is provided by the row in the knowledge map.

### 4.4. Artifact indexing system

Format:

```text
{{SUBJ}}-{{TYPE}}-{{NN}}-{{slug}}
```

Subject codes (examples, learner-defined):

| Code | Subject |
|---|---|
| {{SUBJ_1}} | {{subject_1}} |
| {{SUBJ_2}} | {{subject_2}} |
| {{SUBJ_3}} | {{subject_3}} |
| {{SUBJ_4}} | {{subject_4}} |
| {{SUBJ_5}} | {{subject_5}} |
| {{SUBJ_PROJ}} | {{project}} |

Allowed types:

| Type | Meaning |
|---|---|
| `NOTE` | Concept note, theory, explanation |
| `DRL` | Drill, practicum, task or group of tasks |
| `UNT` | Learning unit |
| `ADR` | Project or architecture decision record |
| `EXM` | Exam, mini-exam, transition check |

Rules:

- `NN` is chosen by the learner.
- The AI asks for `artifact_id` when it needs it.
- `artifact_id` is immutable.
- After deletion the number is not reused.
- `slug` is English, lowercase, kebab-case, 2–5 words.
- Filename always equals `artifact_id.md`.

Placement:

| Subject | NOTE | DRL / UNT / EXM |
|---|---|---|
| {{subject_1}} | `{{subject_1}}/Notes/` | `{{subject_1}}/Tasks/` or `{{subject_1}}/Tests/` |
| {{subject_2}} | `{{subject_2}}/Notes/` | `{{subject_2}}/Tests/` |
| {{subject_3}} | `{{subject_3}}/Notes/` | `{{subject_3}}/Tests/` |
| {{subject_4}} | `{{subject_4}}/Notes/` | `{{subject_4}}/Tests/` |
| {{subject_5}} | `{{subject_5}}/Notes/` | `{{subject_5}}/Tests/` |
| {{project}} | inside repository | inside repository |

### 4.5. Universal artifact core

All subjects share one core:

```text
## Model

## Independent work

## Verification

## Errors and causes

## Written answers to mentor

## Connections and next step
```

Block meaning:

| Block | What is recorded |
|---|---|
| Model | how the topic or task is structured: concept, formula, algorithm, system, rule |
| Independent work | what the learner did alone: solution, code, commands, exercises, output, experiment |
| Verification | how correctness was confirmed: substitution, run, exit status, test, comparison |
| Errors and causes | error lab: where it broke, why, how to fix |
| Written answers to mentor | understanding of mechanism, boundaries, traps, checks |
| Connections and next step | map, related topics, debt, next topic, backlog |

Rules:

- `NOTE` feeds future practical confirmation but alone does not produce `mastered`.
- `DRL`, `UNT`, `EXM` may end with `PETITION`.
- A subject adapter adds specific blocks but does not break the universal core.

### 4.6. Conditional block library

Conditional blocks are inserted only when the task or topic type requires them.

| Block | When needed | Subject archetype |
|---|---|---|
| State table | mixture, alloy, concentration, evaporation | quantitative modeling |
| Motion diagram / speed-time-distance table | motion problems | quantitative modeling |
| Work table | rate-time-volume problems | quantitative modeling |
| Base-change-total table | percent, price, tax | quantitative modeling |
| Domain / graph | functions, equations with analysis | quantitative modeling |
| Numeric check | any numeric answer | quantitative, conceptual |
| Mini-script in host language | meaningful formula or algorithm check | quantitative, conceptual |
| Prediction before run | code, command, experiment | programming, practical, conceptual |
| Solution levels 0 / 1 / 2 | task with multiple approaches | programming |
| Edge cases | input, conditions, loops, functions, files | programming |
| Style / lint pass | any code | programming |
| Commit / PR | code in repository | programming, project |
| Command anatomy | new command | practical / command-line |
| Command, output, exit status | practical scenario | practical / command-line |
| Break intentionally | practical, programming, conceptual, quantitative | several |
| Verification, not decoration | result check, not pretty output | practical / command-line |
| Form / meaning / usage | grammar | language |
| Typical learner errors | grammar, lexis | language |
| Exercises SB / WB | practice | language |
| Warm-up recall | interval repetition | language, skill |
| Mini-experiment | concept demonstration | conceptual |
| Connection to other subjects | concept in the machine | conceptual |
| Milestone / current level | project | project |
| Backlog / not now | project outruns level | project |

Principle:

```text
The mentor does not hand a ready model as a default template.
The mentor teaches the learner to build the model independently.
A ready model is allowed only as a mentor example after the learner's independent attempt or by explicit request.
A mentor example is not evidence of mastered.
```

### 4.7. PETITION form

`PETITION` is the official request from the subject chat to move an artifact to `mastered`.

```text
PETITION
id: {{artifact_id}}
subj: {{SUBJ}}
type: {{DRL|UNT|EXM}}
req: mastered
crit: independent={{yes|no}} | test={{result|tasks}} | written=mentor_approved | verify={{method}} | error={{yes|no|na}}
note: {{optional}}
```

Rules for AI:

- `independent=yes` is mandatory.
- `written=mentor_approved` is mandatory.
- `test` is mandatory: test result or completed tasks.
- `verify` is mandatory: numeric check, code run, exit status, answer check, experiment output, or equivalent.
- `error=na` is allowed only where error analysis is not applicable, for example a pure `EXM`.
- If any element is missing, the subject chat does not submit a `PETITION`.
- The subject chat does not set `mastered` in the map. It only proposes it.

### 4.8. Daily log template

`daily_log` is the learner's only regular form.

Template file:

```text
Daily/Templates/daily_log.md
```

```text
date: {{date:YYYY-MM-DD}}
mode: A | B
plan: {{subjects_planned_today}}
sleep: {{sleep}} | walk: {{walk}} | sport: {{sport}}

## Maintenance

| Tool | progress |
|---|---|
| {{maintenance_tool}} | — |

| Tool | new items | reviewed items |
|---|---:|---:|
| {{spaced_tool_1}} | — | — |
| {{spaced_tool_2}} | — | — |
| {{spaced_tool_3}} | — | — |

## Studies

| Subject | h | artifact_id | proposed | note |
|---|---:|---|---|---|
| {{SUBJ}} | — | — | — | — |

## Log

well:  
difficult:  
debt:  
change:  

## Petitions
```

Filling rules:

- `proposed` = `PETITION` if the subject chat issued a petition.
- `note` — short human remark.
- Manual `evidence` field is absent.
- Debts may be written in `Log` via the `debt:` prefix.
- `Petitions` holds official blocks from subject chats.
- The project subject participates in `daily_log` but has no knowledge map.
- If a subject was not touched, the row may stay empty or be omitted.

### 4.9. Dispatcher state and DISPATCHER_RESPONSE

File:

```text
Daily/Dispatcher_state.md
```

Purpose:

- operational snapshot of the system;
- context transfer between chats;
- storage of the latest `DISPATCHER_RESPONSE`;
- queue of debts, petitions, recall, flags, next actions.

Important:

- `Dispatcher_state.md` is generated fully by the AI dispatcher.
- The learner copies/pastes the generated block into the local file.
- `Dispatcher_state.md` is not the source of truth for topic status.
- Knowledge maps remain the source of truth.
- On divergence between `Dispatcher_state.md` and a map, the map overrides.

Template:

```text
# Dispatcher State

generated_by: dispatcher_ai
generated_at: {{YYYY-MM-DD HH:MM}}
purpose: handover_snapshot
source_of_truth: {{subject}}_map_of_content.md
warning: not a status registry; maps override this file

## Last response

DISPATCHER_RESPONSE
date: {{YYYY-MM-DD}}
confirm: [{{artifact_id, ...}}]
needs: [{{artifact_id: missing ..., ...}}]
flags: [{{debt/risk, ...}}]
next: [{{action, ...}}]
map_rows:
| artifact_id | Topic | Level | Status | Proposed | Confirmed | Evidence |
|---|---|---|---|---|---|---|

## Handoff

| kind | subject | ref | state | next action |
|---|---|---|---|---|
```

Allowed `kind`:

| kind | Meaning |
|---|---|
| `focus` | current working topic or artifact |
| `debt` | unclosed practicum or missed block |
| `petition` | petition awaiting dispatcher confirmation |
| `confirmed` | confirmed status already inserted into a map |
| `flag` | risk, imbalance, sequence violation |
| `recall` | planned interval repetition, especially for language or skill maintenance |

Dispatcher rules:

- The dispatcher confirms `mastered` only on the basis of a `PETITION` and artifact existence.
- Without a `PETITION` the dispatcher does not set `mastered`.
- Without an artifact the dispatcher does not create a `map_row`.
- When data is missing the answer is always `NEEDS`, never an invented `CONFIRM`.
- `map_rows` are generated by the dispatcher.
- The learner pastes `map_rows` into the corresponding knowledge maps.
- The learner pastes the updated `Dispatcher_state` into the local file.

### 4.10. Migration and inventory protocol

The system starts from empty knowledge maps.

Old files are not mass-renamed.

Principle:

```text
Migrate just-in-time: only what is taken into work.
A legacy file without artifact_id is not a defect until taken into migration.
A new file with artifact_id without a map row is a defect.
```

Migration order for one old file:

1. Open the old note or practicum.
2. Determine the verifiable learning unit.
3. Assign `artifact_id`.
4. Create the file with the index header.
5. Rework the body per the universal core and subject adapter.
6. Pass the practicum or drill in the working chat.
7. Obtain written answers and verification.
8. If criteria are met, the subject chat issues `PETITION`.
9. The learner pastes `PETITION` into `daily_log`.
10. The dispatcher confirms or returns `NEEDS`.
11. The learner pastes the ready row into the knowledge map.

Old status conversion:

| Old status | New status |
|---|---|
| notes ready but no practicum | `unverified` or `in_progress` |
| topic actively worked now | `in_progress` |
| old passed without verifiable trail | `unverified` |
| old passed with clear artifact and check | fast `PETITION` possible |

---

## 5. Subject-adapter framework

### 5.1. Purpose

Each subject has a different shape and a different verification method. The framework below shows how to build an adapter, not a fixed set of subjects.

For every subject the learner defines:

- allowed artifact types;
- folder placement;
- mandatory adapter blocks on top of the universal core;
- conditional blocks by task class;
- `PETITION` criteria specific to the subject;
- progression levels and transition criteria;
- mentor constraints.

### 5.2. Adapter matrix

| Subject archetype | Typical types | Placement | Mandatory adapter | PETITION for |
|---|---|---|---|---|
| Quantitative / problem-solving | `NOTE`, `DRL`, `EXM` | `Notes/`, `Tasks/` | model, solution, check, error lab, written answers | `DRL`, `EXM` |
| Programming | `NOTE`, `DRL`, `EXM` | `Notes/`, `Tests/` | prediction before run, hand-written code, edge cases, style, commit | `DRL`, `EXM` |
| Practical / command-line | `NOTE`, `UNT`, `EXM` | `Notes/`, `Tests/` | command anatomy, output, exit status, break intentionally, verification | `UNT`, `EXM` |
| Language / skill | `NOTE`, `UNT`, `DRL`, `EXM` | `Notes/`, `Tests/` | form, meaning, usage, exercises, test, error lab, warm-up recall | `UNT`, `DRL`, `EXM` |
| Conceptual science | `NOTE`, `DRL`, `EXM` | `Notes/`, `Tests/` | concept, mini-experiment, prediction, output, explanation, cross-subject link | `DRL`, `EXM` |
| Project | `NOTE`, `ADR`, `DRL`, `EXM` | inside repository | spec, roadmap, milestone, current level, runnable code, commit, backlog | no map; tracked via repo and daily log |

### 5.3. Quantitative / problem-solving adapter

Types: `NOTE`, `DRL`, `EXM`.

Base frame:

```text
## Model

## Independent work

## Verification

## Errors and causes

## Written answers to mentor

## Connections and next step
```

For `DRL`, the `Model` block must include:

- task type;
- given / find;
- key property, formula, or principle;
- variable choice;
- why this method;
- which quantities are preserved or changed.

Conditional blocks by task class:

| Task class | Conditional block |
|---|---|
| mixture, alloy, concentration, evaporation | state table |
| motion | motion diagram or speed-time-distance table |
| work | rate-time-volume table |
| percent, price, tax | base-change-total table |
| functions, equations with analysis | domain, graph, range |
| combinatorics, digits, residues | enumeration, digit check, residue check |

Rule:

```text
The learner builds the table, diagram, graph, or balance.
The mentor checks and guides.
A ready sample is allowed only as a mentor example.
```

Verification for numeric and model tasks:

- substitution of the answer into the original equation;
- inverse problem;
- balance check of mass, substance, money, time;
- dimension check;
- plausibility estimate;
- mini-script in the host language when it meaningfully checks a formula or algorithm.

The mini-script is not mandatory for every micro-topic. It is used where it genuinely checks a formula, algorithm, or numeric model.

Written answers to mentor are mandatory. The mentor determines the number, wording, and depth of questions based on topic, task type, and learner level. Questions must probe:

- why this method;
- where the boundary of applicability;
- what changes if the condition changes;
- where a typical error sits;
- how to check the result.

In `PETITION` the mark is `written=mentor_approved`.

Mentor constraints:

1. The source is the arbiter. If AI contradicts the textbook or notes, the source wins.
2. The AI may compose typical tasks on request. Forbidden is not generating tasks, but generating incorrect, premature, or source-substituting tasks.
3. An AI task must be verifiable: condition, solution, and check must be correct.
4. An AI task does not substitute the source without the learner's knowledge. If generated by AI, mark it as AI variant.
5. For `mastered` the active source is preferred. AI variant is allowed if the mentor confirmed equivalence by class, difficulty, and verified skill.
6. Numeric check is mandatory for computational answers.
7. The mentor does not give the ready solution first. The learner tries first; the mentor guides with questions.
8. The mentor does not hand a ready model as a template when the learner can build it. The learner builds the model; the mentor checks.

`PETITION` criteria:

```text
independent=yes
test=5–10 questions or completed tasks
written=mentor_approved
verify=numeric check / substitution / balance check / host-script if applicable
error=yes or na
```

Granularity: one artifact may be one task, a group of homogeneous tasks, one paragraph or micro-topic, or a mini-exam. The criterion: the artifact must be small enough to issue a separate `PETITION` and, on error, return a specific zone to `in_progress`, not the whole chapter.

### 5.4. Programming adapter

Types: `NOTE`, `DRL`, `EXM`.

Philosophy: programming is not about producing correct output. It is about the ability to predict and explain code behavior.

```text
Working code is not the goal.
The goal is code whose behavior you can predict and explain on any input, including garbage.
```

Base frame:

```text
## Model

## Prediction before run

## Independent work

## Verification

## Errors and causes

## Written answers to mentor

## Connections and next step
```

Prediction before run is mandatory for tasks with code:

```text
input → prediction → actual output → matched? → why
```

If the learner cannot predict the output before running, the learner is not controlling the code but guessing.

Code is written by hand. No copying. Even if the learner saw a solution, it must be retyped and explained.

Three-level method, where meaningful:

| Level | Name | Meaning |
|---|---|---|
| 0 | Brute force | direct enumeration, works but scales poorly |
| 1 | Pattern / logic | regularity, modulo, boolean inversion |
| 2 | Idiomatic | built-in tools, readability, idiom |

The ceiling of level 2 depends on the current progression level.

| Progression level | Allowed in drill |
|---|---|
| {{L1}} | {{L1_topics}} |
| {{L2}} | {{L2_topics}} |
| {{L3}} | {{L3_topics}} |
| {{L4}} | {{L4_topics}} |
| {{L5}} | {{L5_topics}} |
| {{L6}} | {{L6_topics}} |

If level 2 requires apparatus above the current level, it is marked as a ceiling and not required for `mastered`. Demanding idiomatic code too early creates a false debt.

Quality lab, separate from the main condition:

Edge cases:

- empty value if applicable;
- zero;
- negatives;
- range boundaries;
- malformed data;
- very large data if applicable.

Style pass:

- naming;
- indentation;
- line length;
- blank lines;
- clarity;
- absence of needless complexity.

Style is a quality layer, not a separate topic.

Stuck protocol: if the learner is stuck for more than 15 minutes, the learner writes `Stuck. Need a hint.` Before that, the learner records in writing:

- which approaches were tried;
- why they failed;
- where understanding broke.

The mentor gives a guiding question, analogy, pseudocode, or direction of thought. The mentor does not give ready code.

Mentor constraints:

1. Do not write the ready solution first.
2. Do not hand ready refactoring.
3. Check prediction before run.
4. Demand hand-written code.
5. Analyze edge cases.
6. Compare approaches, not just praise working code.
7. Respect the current progression level.
8. Do not pull the learner into apparatus of a later phase without explicit goal and permission.
9. Help link the subject to other subjects and the project.
10. Do not substitute the source without the learner's knowledge.

The AI may generate tasks. A correct AI task must:

- belong to the current level;
- use only learned apparatus;
- have verifiable input/output;
- not introduce a new topic without explicit request;
- be equivalent by class to the source;
- be marked as AI variant if not from the source.

The active course is the source and progression, but a passed lesson is not `mastered`. `mastered` comes only through practicum, drill, prediction, edge cases, written answers, and dispatcher confirmation. Supporting books are depth and reference, not route replacement.

Repository link:

- study tasks: commit in `{{repo}}/code/`;
- project tasks: commit in `{{project_repo}}`.

A commit is a trail of independent work, not a ritual.

Progression and transition criteria:

| Level | Topics | Transition criterion |
|---|---|---|
| {{L1}} | {{L1_topics}} | {{L1_criterion}} |
| {{L2}} | {{L2_topics}} | {{L2_criterion}} |
| {{L3}} | {{L3_topics}} | {{L3_criterion}} |
| {{L4}} | {{L4_topics}} | {{L4_criterion}} |
| {{L5}} | {{L5_topics}} | {{L5_criterion}} |
| {{L6}} | {{L6_topics}} | {{L6_criterion}} |

Apparatus of the next phase is not part of the current phase.

Mini-exams are type `EXM`. Format per level is defined by the learner. An error on a `mastered` topic removes the status and returns the topic to `in_progress`. A new level opens only after PASS of the corresponding exam.

`PETITION` criteria:

```text
independent=yes
test=tasks completed / test result
written=mentor_approved
verify=code run + prediction check + edge cases
error=yes or na if error lab not applicable
```

### 5.5. Practical / command-line adapter

Types: `NOTE`, `UNT`, `EXM`.

Philosophy: the terminal is the primary interface to the system. The goal is to bring base operations to muscle memory while understanding paths, filesystem objects, exit status, and streams.

Four mandatory layers:

| Layer | Provides |
|---|---|
| Semantic | why the command exists, what engineering task it solves |
| System | cwd, paths, arguments, flags, stdout, stderr, exit status |
| Verification | independent result check, not only visual output |
| Reflective | error analysis, deliberate break, rule in own words |

Base frame:

```text
## System model

## Command anatomy

## Practice

## Result verification

## Errors and causes

## Written answers to mentor

## Connections and next step
```

Command line model:

```text
command [options] [operands]
```

- `command` — program or shell builtin;
- `options` / `flags` — behavior modifiers;
- `operands` / `arguments` — objects: files, directories, strings.

The shell parses the line, expands paths and special characters, then runs the command. The command receives arguments and returns an exit status.

Exit status literacy from the first level:

- after key commands run `echo $?`;
- `0` means success;
- non-zero means error;
- "terminal printed nothing" does not mean "nothing happened";
- a stderr message is a diagnosis, not decoration.

Verification, not decoration. For each unit at least one independent check:

- `ls -ld path`;
- `ls path`;
- `find path -maxdepth 1`;
- `test -d path && echo DIR_OK`;
- `test -f path && echo FILE_OK`;
- `echo $?`;
- comparison of expected and actual structure.

Practice format:

- 5–9 tasks of increasing difficulty;
- at least one check task, not only creation;
- at least one "break intentionally and analyze";
- at least one question on exit status;
- at least one question on absolute vs relative path if the topic allows.

Each task fields:

```text
### Task N: [name]

**Goal:**  
**Expected result:**  
**Hint:**  
**Verification method:**  
**My command:**  
**Output:**  
**Exit status:**  
**Comment:**  
```

No ready solutions in the main body. The mentor key is issued separately in chat after the report, or as a separate key file if needed.

Scenario safety:

1. All manipulation only in sandbox `{{sandbox}}`.
2. No destructive commands outside the sandbox.
3. Before a wildcard delete, always `ls` with the same pattern first.
4. In study scenarios prefer interactive flags by default.
5. Privilege escalation only on explicit study need.
6. If the topic touches permissions, first explain the owner / group / other model and bits, then commands.

Progression:

| Level | Topics | Transition criterion |
|---|---|---|
| {{L1}} | {{L1_topics}} | {{L1_criterion}} |
| {{L2}} | {{L2_topics}} | {{L2_criterion}} |
| {{L3}} | {{L3_topics}} | {{L3_criterion}} |
| {{L4}} | {{L4_topics}} | {{L4_criterion}} |

Mentor constraints: explain not "which command to type" but how the system works; teach to predict result before execution; demand exit status and independent checks; give tasks where naive execution breaks; do not solve for the learner; do not put the ready key in the main unit body.

The AI may generate scenarios. A correct AI scenario must: belong to the current level; use only learned apparatus; be safe; run in the sandbox; have a verifiable result; not substitute the source without the learner's knowledge; on divergence with the source or agreed scenario, the source or agreed scenario wins. Mark AI-generated scenarios as AI scenario.

`PETITION` criteria:

```text
independent=yes
test=tasks completed / scenario passed
written=mentor_approved
verify=exit status + independent check
error=yes
```

For this archetype `error=yes` is practically mandatory, because a command-line subject without deliberate break and analysis becomes command memorization.

### 5.6. Language / skill adapter

Types: `NOTE`, `UNT`, `DRL`, `EXM`.

Philosophy: a language is a practical skill. It requires regular retrieval, written practice, interval repetition, and understanding of form, meaning, and context.

Base frame:

```text
## Language model

## Independent work

## Verification

## Errors and causes

## Written answers to mentor

## Connections and next step
```

For grammar units the `Language model` block expands through:

- form;
- meaning;
- when used;
- typical learner errors;
- practice;
- test;
- work on errors.

Mandatory semantic blocks for grammar units:

| Block | What is recorded |
|---|---|
| Form | how the construction is built: affirmative, negative, question, auxiliaries, endings, word order, spelling |
| Meaning | what the expression conveys: fact, habit, schedule, state, past, present, future, possibility, obligation |
| When used | real contexts, difference from a similar construction, where translation from the native language breaks |
| Typical errors | 3–5 pairs wrong → correct → why |
| Practice | exercises from the source done independently |
| Test | short check of form, meaning, typical errors |
| Work on errors | analysis of own errors |

Conditional blocks by lesson type:

| Lesson type | Conditional block |
|---|---|
| grammar | form / meaning / usage |
| lexis | semantic field / collocations / typical errors |
| reading | prediction by title / information search / written retell |
| listening | prediction / first listen / second listen / detail check |
| writing | draft / self-check / correction by criteria |
| dialogue | context / speech function / useful language / written practice |

Oral practice is not a system requirement. If a unit includes speaking as part of the textbook, the mentor may use it as context but does not demand it as a mandatory `mastered` trail.

Working cycle: source load → note generation → independent practice → warm-up recall → test and written answers → petition → fixation.

Step 1. Source load. The learner sends screenshots or photos of the active unit pages: student book, workbook, teacher's guide (for mentor context only, not for handing out answers), audio/video by title or timecodes if needed. The learner states: subject and source; artifact type needed (`NOTE`, `UNT`, `DRL`, `EXM`); `artifact_id` if chosen, or asks the mentor to request the next `NN`.

Step 2. Note generation. The mentor creates a note per the standard below. The note explains grammar but contains no ready answers to textbook exercises.

Step 3. Independent practice. The learner does SB/WB exercises alone. The mentor does not give answers to textbook tasks. The mentor checks the learner's submitted answers and explains errors through form, meaning, context, and typical learner errors.

Step 4. Warm-up recall. Before a new unit — 5–10 minutes, 2–3 short written tasks on previously passed topics. Warm-up does not replace practicum and does not produce `mastered`.

Step 5. Test and written answers. Within `UNT`/`DRL`/`EXM` — a short test and written answers to the mentor. Question wording is determined by the mentor; no hard count is set.

Step 6. PETITION. If criteria are met, the mentor generates `PETITION`. The learner pastes it into `daily_log`. The dispatcher confirms or returns `NEEDS`.

Step 7. Fixation. The learner pastes the ready row from `DISPATCHER_RESPONSE` into the language map. The map is the source of truth.

Note quality standard for AI generation:

Mandatory structure:

```text
## Main idea
## Form and structure
## When used
## Typical learner errors
## Practice
## Test
## Work on errors
```

Content must cover at least four levels:

1. Form — how it is formed; which elements are mandatory; what changes by person, number, tense, negation, question.
2. Meaning — what it expresses; in which situations it is natural; how it differs from a similar construction.
3. Application — examples in realistic contexts; examples close to exercises; at least one example with a typical error and correction.
4. Error mechanics — where the learner will likely break; why the error arises; how to self-check before sending.

Oral practice is not a mandatory note level.

Pedagogical constraints:

1. Do not give ready answers to SB/WB/textbook exercises.
2. Do not copy textbook examples as "task solutions".
3. Do not replace explanation with simple translation.
4. Do not stop at a formula like `Subject + verb + s`.
5. Do not emit a note without examples, exceptions, and typical errors.
6. Do not write internal remarks like "here I will add", "check later", "could improve".
7. If the learner asks for a single copyable block, return only the note in one block, without remarks inside.
8. If mentor comments are needed, place them after the block, not inside the note.
9. Do not substitute the source without the learner's knowledge.
10. AI variant exercises are allowed only if they match the current unit, lexis, and grammar, and are marked as AI variant.

Technical Markdown standard: follows general conventions §0.5–§0.7. Key points:

- a single copyable block without stray closing fences;
- if inner examples need `text`/`bash`/`python` blocks and the note is sent as one copyable block, the outer block uses an increased backtick count so inner triple blocks do not break copying;
- if the outer block is a plain triple, inner triple blocks are forbidden;
- index header correct: `artifact_id` in H1, `source`, `date`;
- no YAML-frontmatter;
- headings not merged with text;
- tables with correct separator and equal cell count;
- lists not broken by indentation;
- no broken words, stray characters, floating blocks;
- if the learner asks for "one block to copy", the AI returns only that block without internal remarks.

Send format by default:

1. short intro phrase if needed;
2. one markdown block with the note;
3. a short next step.

If the learner explicitly asks "only the block" or "single copyable block", the AI sends only the markdown block without intro or closing comments.

Acceptance criterion for a note:

1. copies into the vault in one motion without manual repair;
2. index header correct;
3. main idea, form, meaning, application, typical errors present;
4. test and practice present;
5. no ready answers to textbook exercises;
6. no broken Markdown;
7. no internal AI remarks;
8. the note helps do tasks independently, not replaces independent work;
9. `NOTE` alone does not produce `mastered`; `mastered` only via `UNT`/`DRL`/`EXM` + `PETITION` + dispatcher.

Broken-note repair follows §0.8: regenerate the whole note, preserve structure, eliminate the Markdown cause, return one intact block.

Warm-up recall: every language session begins with 5–10 minutes of short written recall of previously passed grammar topics. The mentor picks 2–3 points: 1 from the last session; 1 aged 3–7 days; 1 aged 14–30 days if available. Format: correct an error; choose the form; build a question; translate a mini-phrase; complete a sentence; explain why a variant is wrong. Results:

| Result | Action |
|---|---|
| Confident answer | topic stays in current status |
| Forgot but fixed with a hint | topic may stay `mastered` but gets a `recall` flag |
| Systemic error or cannot explain | topic returns to `in_progress` or `unverified`; new unit does not open until fixed |

Warm-up recall does not create separate artifacts, does not add map columns, is not a basis for `mastered`, is recorded in `daily_log` briefly if needed, and the repetition queue is kept in `Dispatcher_state.md` as `kind: recall`.

Sequence rule: a new unit opens only after `mastered` confirmation of the previous. If there is an open debt: new unit does not open; debt closes first; then progression moves.

Maintenance background (spaced tools, audio trainers) supports the language but does not replace practicum and does not produce `mastered` for a grammar unit. `mastered` comes only through `UNT`, `DRL`, or `EXM` and dispatcher confirmation.

`PETITION` criteria:

```text
independent=yes
test=exercises completed / test result
written=mentor_approved
verify=answer check / self-correction / source comparison
error=yes or na if no errors occurred
```

### 5.7. Conceptual science adapter

Types: `NOTE`, `DRL`, `EXM`.

Philosophy: conceptual science is not a textbook retelling. It is the ability to see a concept in the machine.

```text
read → predicted → ran → got output → explained divergence → linked to other subjects
```

If a concept cannot be shown via a mini-experiment, the mentor explains why and translates it into a model, scheme, or manual calculation.

Base frame:

```text
## Model

## Independent work

## Verification

## Errors and causes

## Written answers to mentor

## Connections and next step
```

Mandatory layers:

| Layer | What is done |
|---|---|
| Concept | what it is, why an engineer needs it, where it appears in other subjects |
| Mini-experiment | host-language script, command, manual calculation, truth table, trace table |
| Prediction before run | input → prediction → actual output → matched? → why |
| Divergence explanation | where the model was wrong, which system property was not accounted, how to fix understanding |
| Cross-subject link | concept → programming, → practical, → quantitative, → project |

Conditional blocks by topic type:

| Topic type | Conditional block |
|---|---|
| algorithms | algorithm forms, trace table |
| numeral systems | conversion table, manual calculation |
| logic | truth table |
| memory | stack/heap scheme, size in bytes |
| data structures | storage model, operations |
| information encoding | bits, bytes, alphabet power |
| networks | transmission model, addressing, packets |
| computer architecture | components, data flow |

Mentor constraints: do not replace the textbook with retelling; help the learner design the mini-experiment independently; check prediction before run; demand explanation of actual output; link the concept to other subjects; do not introduce apparatus above the current level; may generate correct AI experiments; on divergence with the source, the source or agreed scenario wins.

A correct AI task must: belong to the current topic; use only learned apparatus; have verifiable output; not substitute the source without the learner's knowledge; be marked as AI experiment if not from the textbook.

`PETITION` criteria:

```text
independent=yes
test=experiment completed / tasks result
written=mentor_approved
verify=prediction + actual output + explanation
error=yes or na if error lab not applicable
```


---

## 6. Rules

| № | Rule | Basis |
|---|---|---|
| 1 | Strategic focus rule: the learner defines one primary track and forbids premature diversification until a defined milestone. | Do not scatter resource. |
| 2 | Secondary domains not opened until the primary track is secured. | Separate worlds. |
| 3 | Framework selection rule: the learner chooses one framework per phase and justifies it by discipline requirements. | Type and async discipline. |
| 4 | Clean-sheet rule for the active course. | Solve by hand and head. |
| 5 | Daily maintenance: spaced tools + audio trainer. | Language and terms. Repetition mandatory, new items when possible. |
| 6 | Commit to remote. | As progress occurs and when an interesting task is solved. |
| 7 | Sleep: preparation {{prep_time}}, lights out {{bed_time}}, wake {{wake_time}}. | Memory consolidation. |
| 8 | Walk {{walk_min}}–{{walk_max}} minutes. | Oxygen for the brain. |
| 9 | No code copying. | Type by hand. |
| 10 | Subject balance. | All disciplines move in parallel. Skipping a subject more than 2 days in a row is a signal for review. |
| 11 | Daily `daily_log` → dispatcher. | The only regular learner form. |
| 12 | Config review first {{review_day}} of month, {{review_min}} min. | Config is a living document. |
| 13 | Practicum mandatory. | Without a passed practicum a topic does not become `mastered`. |
| 14 | A note without a link to a knowledge map does not exist. | Map = source of truth. |
| 15 | Schedule operational integrity. | A missed block is not compensated at night and does not cancel sleep/walk. |
| 16 | New unit only after closing the previous debt for practical and language subjects. | Prevents accumulation of unverified layers. |
| 17 | Source is the arbiter, not AI. | On AI vs textbook divergence, the textbook wins. |
| 18 | Numeric check mandatory for computational answers. | Without check — not `mastered`. |
| 19 | Subject chat proposes status, dispatcher confirms. | Separation of work and control. |
| 20 | `artifact_id` immutable. | Links in maps must not break. |
| 21 | Statuses: `in_progress` → `unverified` → `mastered`. | Single working progress model. |
| 22 | `NOTE` does not give `mastered`. | A note is material, not proof of learning. |
| 23 | Written answers to mentor mandatory. | They probe mechanism understanding. |
| 24 | Manual `evidence` filling in `daily_log` cancelled. | Trails are fixed by mentor and dispatcher. |
| 25 | `Dispatcher_state` generated by AI, learner pastes locally. | Seamless handover without context loss. |
| 26 | Knowledge maps are the source of truth. | `Dispatcher_state` does not duplicate statuses as a registry. |
| 27 | A debt is closed in the next block of the same subject. | New topic does not open before the debt is closed. |
| 28 | AI may generate correct AI variants. | Forbidden is not generating, but generating incorrectly or prematurely. |
| 29 | The project has no knowledge map and does not outrun the primary level. | The project is an integrator, not a sixth endless elective. |
| 30 | Migration goes just-in-time. | Do not redo the whole archive at once. |

---

## 7. Schedule

### 7.1. Base day grid
### 7.2. Weekly grid

### 7.3. Failure and shift protocol

- Keep a 5–10 minute buffer between dense blocks.
- If a block is missed for a valid reason, mark it in `daily_log` as `missed` with a cause.
- Do not move it to night and do not cut sleep, walk, exercise for it.
- A `missed` block moves to the nearest free slot of the same day or is fixed as a debt.
- A debt is closed in the next block of the same subject.
- A new topic of the subject does not open until the debt is closed.
- On 2+ consecutive misses or debt accumulation over 3 days — review with the dispatcher.

---

## 8. AI mentor protocol

### 8.1. Multi-chat topology

The system runs through several independent chats.

Roles:

| Chat | Function | Constraint |
|---|---|---|
| Subject chat {{subject_1}} | Deep work on {{subject_1}} | Does not set `mastered`, only `PETITION` |
| Subject chat {{subject_2}} | Deep work on {{subject_2}} | Does not set `mastered`, only `PETITION` |
| Subject chat {{subject_3}} | Deep work on {{subject_3}} | Does not set `mastered`, only `PETITION` |
| Subject chat {{subject_4}} | Deep work on {{subject_4}} | Does not set `mastered`, only `PETITION` |
| Subject chat {{subject_5}} | Deep work on {{subject_5}} | Does not set `mastered`, only `PETITION` |
| Project chat | Work with repository and product | No knowledge map, does not give `mastered` |
| Dispatcher | Gate control, validation, balance | Confirms `mastered`, forms `Dispatcher_state` |

### 8.2. Definition of Ready for a subject chat

Before a session the subject chat must receive:

- `MASTER_CONFIG`;
- its knowledge map;
- the current `artifact_id` or topic;
- the task condition from the source, if the task is taken from textbook, course, practice platform, or specification.

Rule:

```text
The mentor does not reconstruct the condition from memory.
If the condition is not provided, the mentor asks for the source, screenshot, number, or text.
```

AI may generate AI variants but must mark them and check against the current level and source.

### 8.3. Working cycle

```text
subject chat → artifact → practice → written answers → PETITION
learner → daily_log → Petitions
dispatcher → DISPATCHER_RESPONSE → map_rows → Dispatcher_state
learner → pastes map_rows into maps → pastes Dispatcher_state into local file
knowledge maps → source of truth
```

### 8.4. Dispatcher response format

The dispatcher answers compactly and service-wise.

Form:

```text
DISPATCHER_RESPONSE
date: {{YYYY-MM-DD}}
confirm: [{{artifact_id, ...}}]
needs: [{{artifact_id: missing ..., ...}}]
flags: [{{debt/risk, ...}}]
next: [{{action, ...}}]
map_rows:
| artifact_id | Topic | Level | Status | Proposed | Confirmed | Evidence |
|---|---|---|---|---|---|---|

dispatcher_state:
# Dispatcher State
...
```

Rules:

- `confirm` — confirmed `mastered`.
- `needs` — what is missing for a petition.
- `flags` — debts, imbalances, risks.
- `next` — what to do in the next block.
- `map_rows` — ready rows for insertion into knowledge maps.
- `dispatcher_state` — operational snapshot for `Daily/Dispatcher_state.md`.

### 8.5. Dispatcher validation checklist

The dispatcher confirms `mastered` only if:

1. The artifact exists by name `artifact_id.md`.
2. A map row exists or will be created via `map_rows`.
3. `artifact_id` matches the filename.
4. There is a `PETITION` from the subject chat.
5. `independent=yes`.
6. `written=mentor_approved`.
7. There is `test` or completed tasks.
8. There is `verify`.
9. No sequence violation.
10. No contradiction: for example `mastered` but `daily_log` shows `missed` without closure.

If something is missing, the dispatcher answers `NEEDS` and names the concrete missing element.

### 8.6. Exam sessions

Short check:

- once every {{exam_period}};
- {{exam_min}}–{{exam_max}} minutes;
- {{exam_tasks}} tasks of the current phase;
- written.

An error on a `mastered` topic removes the status and returns it to `in_progress`.

Full phase-transition exam:

- practical block: live tasks (write code / solve in chat, not copying);
- understanding questions: written answers to {{exam_questions}} mentor questions;
- verdict: `PASS` or `RETRY`.

The project block is not separated: the project is visible in the repository, roadmap, commits, and working code.

### 8.7. Proactive handover

The AI estimates dialog length.

At roughly 70–80% context fill the AI must warn:

```text
Context window is filling. A new MASTER_CONFIG and current state must be saved.
```

Action:

- AI generates the current `MASTER_CONFIG`;
- updates `Dispatcher_state`;
- lists open debts and pending petitions;
- learner saves files;
- a new chat starts with `MASTER_CONFIG` + `Dispatcher_state` + the needed map.

---

## 9. Summary

I, {{learner_name}}, build a career from {{primary_track}} to {{secondary_track}}.

The foundation is formed algorithmic engineering thinking.

All subjects develop in balance and complement each other:

- {{subject_a}} feeds {{subject_b}};
- {{subject_b}} gives understanding under {{subject_c}};
- {{subject_d}} makes infrastructure tangible;
- {{subject_e}} accelerates access to knowledge;
- {{project}} gathers skills into a product.

Notes and knowledge maps are my second memory.

It works only through practicum:

- independent work;
- test or tasks;
- written answers to the mentor;
- result verification;
- error analysis.

Subject chats give deep practice.

The dispatcher guarantees that progress is real, not drawn.

Knowledge maps are the source of truth.

I am not rushing. I am building for decades.

---

## Appendix A. Operational snapshot

Snapshot on {{date}}.

Statuses and confirmation dates live in knowledge maps. Here is an operational slice for handover and migration start.

| Subject | Resource | Current focus | State | Next action |
|---|---|---|---|---|
| {{subject_1}} | {{source_1}} | {{focus_1}} | {{state_1}} | {{next_1}} |
| {{subject_2}} | {{source_2}} | {{focus_2}} | {{state_2}} | {{next_2}} |
| {{subject_3}} | {{source_3}} | {{focus_3}} | {{state_3}} | {{next_3}} |
| {{subject_4}} | {{source_4}} | {{focus_4}} | {{state_4}} | {{next_4}} |
| {{subject_5}} | {{source_5}} | {{focus_5}} | {{state_5}} | {{next_5}} |
| {{project}} | {{project_path}} | {{focus_proj}} | {{state_proj}} | {{next_proj}} |

Notes:

- A previously closed topic is confirmed in the new system only after migration, artifact, and dispatcher confirmation.
- The project has no knowledge map. Its progress is visible in the repository.
- All old files before migration remain legacy and are not defects of the new system.