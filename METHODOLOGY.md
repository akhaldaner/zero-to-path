# Methodology

This document describes the system behind zero-to-path — how topics are studied, verified, and tracked. It is public so that it can be examined, questioned, and adapted.

The material being studied is private. The method is not.

## 1. Knowledge maps

For each subject, exactly one file — the knowledge map — acts as the source of truth. Notes hold the material. The map holds what is active, what is verified, and what is at risk.

Every artifact has an immutable ID:

```text
SUBJECT-TYPE-SEQ-slug
```

Rules:

- `SUBJECT` is one of `MATH`, `PY`, `LIN`, `ENG`, `CS`, `FIN`.
- `TYPE` is one of `NOTE`, `DRL`, `UNT`, `ADR`, `EXM`.
- `SEQ` is a three-digit number from `001` to `999`.
- Leading zeros are mandatory.
- `slug` is lowercase kebab-case, usually 2–5 words.
- The filename equals the artifact ID plus `.md`.
- A map row without a file is a defect.
- A new file with an artifact ID without a map row is a defect.
- Legacy files without artifact IDs are not defective until they are taken into migration.
- Artifact IDs are immutable.
- After deletion, a number is not reused.

`Daily/Dispatcher_state.md` is an AI-generated handover snapshot. It is not the source of truth. Knowledge maps override it.

## 2. Three statuses

Every active topic is in exactly one of three states:

| Status | Meaning |
|---|---|
| in_progress | Active work is happening, but the topic is not yet verified. |
| unverified | An artifact exists, but confirmation has not passed or evidence is insufficient. |
| mastered | The subject mentor submitted a petition, and the dispatcher confirmed the topic into the knowledge map. |

There is no `not_started` status inside active maps. Unopened topics remain in the source backlog. `notes_ready` is not a status.

## 3. Mastery criteria

A topic earns `mastered` only through a petition workflow.

The subject mentor may submit a petition only when all of the following are true:

- The learner completed the main work independently.
- There is a test result or a completed set of tasks.
- The learner gave written answers to the mentor, and the mentor approved them as demonstrating understanding.
- There is verification appropriate to the subject: numeric check, code run, exit status, answer check, experiment output, or equivalent.
- Error analysis is present where applicable.
- The required apparatus did not exceed the learner’s current level.
- The sequence rule was not violated.
- The evidence comes from a practical artifact: `DRL`, `UNT`, or `EXM`.

A `NOTE` alone never produces `mastered`. Only `DRL`, `UNT`, or `EXM` artifacts can produce a petition.

The mentor proposes mastery. The dispatcher confirms it. The knowledge map records the confirmed state.

## 4. Mentor role: teacher-guide, not inspector

The subject mentor is a learning counterpart and teacher-guide.

Its duties are:

- explain the mechanism before asking for proof;
- provide sufficient theory, examples, boundaries, and typical traps;
- avoid artificial gaps that force the learner to guess basic concepts;
- keep the scope of the current artifact controlled;
- verify independent work, not rewrite it;
- reject work only through a concrete blocking criterion;
- avoid turning practice into an infinite audit;
- treat `mastered` as sufficient verifiable evidence, not perfection.

The mentor does not have the right to:

- give the final solution first;
- silently expand requirements after a drill has started;
- demand material above the current level as a condition for mastery;
- turn a `NOTE` into a worksheet;
- require written answers inside a `NOTE` as a mastery condition;
- reject work with vague phrases such as “not deep enough” or “redo it” without a concrete criterion.

## 5. Artifact roles

| Type | Role | Produces mastery? |
|---|---|---:|
| NOTE | Explanatory learning material: model, mechanism, examples, boundaries, traps, connections. | No |
| DRL | Drill or practicum: independent work, verification, errors, written answers. | Yes, through petition |
| UNT | Learning unit, especially Linux or English: theory plus practice. | Yes, through petition |
| EXM | Exam or transition check: integration of several topics. | Yes, through petition or verdict |
| ADR | Project or architecture decision record. | No |

The central separation is:

```text
NOTE explains.
DRL verifies.
EXM assembles.
ADR decides.
```

## 6. NOTE quality standard

A `NOTE` is a full explanatory learning artifact. It is not a worksheet, not a test, and not proof of mastery.

A good `NOTE`:

- puts theory before questions;
- explains mechanism before formula, syntax, command, or rule;
- defines new terms at first use;
- may refer briefly to already mastered terms instead of repeating them fully;
- includes worked examples with explanation;
- shows boundaries and typical errors;
- keeps useful material above the current level as `Backlog / полезно позже`;
- does not create hidden debt;
- does not require independent tasks, tests, predictions, or written answers as mastery conditions.

A question inside a `NOTE` is acceptable only as self-check after the explanation. If the question cannot be answered from the `NOTE` or the explicitly cited source, it is a defect unless it is clearly marked as future reference.

## 7. DRL contract

Before starting `DRL`, `UNT`, or `EXM`, the mentor fixes a short contract.

Minimum fields:

```text
DRL_CONTRACT
artifact_id: <artifact_id>
scope: <one micro-topic or narrow skill>
max_tasks: <usually 3–5; UNT usually 5–7>
max_written_questions: <usually 2–3>
verification_method: <run / numeric check / exit status / answer check / experiment output>
error_requirement: <yes / na / one deliberate break>
time_budget: <20–45 min; UNT 45–60 min>
max_revision_cycles: 2
minimum_passing_criteria:
- independent=yes
- tasks completed
- written answers accepted
- verification recorded
- error analyzed or na
```

Rules:

- New requirements are not added after the contract starts.
- If the scope is too large, the mentor proposes a split instead of silently expanding the drill.
- The drill is a micro-proof, not an exam for the whole level.
- Cumulative level criteria, such as “20 tasks for L2”, are not the size of one `DRL`.

## 8. Structured rejection and two-cycle stop rule

The mentor may reject practical work only through a structured request:

```text
REVISION_REQUEST
artifact_id: <artifact_id>
cycle: 1 | 2
blocking_criterion: <independent | test | written | verify | error | sequence | out_of_level | missing_artifact | filename | contract_scope>
minimum_fix: <one concrete action>
new_requirements: none
next_step: <resubmit | petition | debt | split>
```

Vague rejection is invalid.

Maximum revision cycles for one artifact: 2.

After the second revision cycle, the mentor must choose one outcome:

- `PETITION`, if minimum sufficient evidence exists;
- debt / downgrade, if understanding is genuinely not confirmed;
- split, if the artifact mixed too many skills or was too large.

A third endless revision cycle without a dispatcher flag and a new contract is a process defect.

## 9. Petition and dispatcher state

The petition is a compact service record generated by the subject mentor after verifying work. The learner does not compose it manually. The learner inserts it into the daily log.

The petition form is:

```text
PETITION
id: <artifact_id>
subj: <MATH|PY|LIN|ENG|CS>
type: <DRL|UNT|EXM>
req: mastered
source: <textbook / course / task / specification>
level: <L1|L2|L3|L4|L5|L6|—>
crit: independent=<yes|no> | test=<result|tasks> | written=mentor_approved | verify=<method> | error=<yes|no|na>
artifact_path: <relative vault path, if known>
note: <optional short context>
```

Core required fields:

- `id`
- `subj`
- `type`
- `req`
- `crit`

Recommended fields:

- `source`
- `level`
- `artifact_path`
- `note`

The dispatcher is a global navigator, not a second subject examiner.

By default, the dispatcher:

- reads the daily log and petitions;
- validates petition formality;
- checks artifact type, sequence, debts, current level, balance, and process defects;
- does not reread full `DRL`, `UNT`, or `EXM` artifacts;
- may request a short excerpt only on audit trigger;
- generates ready map rows for insertion into knowledge maps;
- generates `Dispatcher_state` only on request or handover trigger.

Standard dispatcher response:

```text
DISPATCHER_RESPONSE
date: YYYY-MM-DD
confirm: [artifact_id, ...]
needs: [artifact_id: missing ..., ...]
flags: [debt/risk/process_defect, ...]
next: [action, ...]
recommend: [short guidance, ...]
map_rows:
| artifact_id | Topic | Level | Status | Proposed | Confirmed | Evidence |
|---|---|---|---|---|---|---|
```

`Dispatcher_state` is formed only when needed, for example:

- the learner explicitly asks for it;
- before a new chat or session;
- at close of week;
- when there are 3+ pending petitions;
- when debts conflict;
- before level or phase transition;
- when a process defect appears;
- when context is filling up.

## 10. Supporting protocols

### Independent work

The learner solves the target task, scenario, or exercise without a ready sample and without step-by-step hints. Hints are allowed only after a documented stuck protocol or an explicit request.

### Error lab

Every practical unit includes at least one deliberate mistake or failure analysis where applicable. The error is the lesson, not the obstacle.

### Warm-up recall

English sessions begin with a short written recall of previous grammar topics. Other subjects may receive recall flags through the dispatcher state when a topic is due or weak.

Warm-up recall does not create separate artifacts and does not replace normal practicum evidence.

### Sequencing rule

A new unit opens only after the previous active debt is closed. This is strict for Linux and English.

### Just-in-time migration

Legacy files are not defective until they are taken into the new system. Migration happens one artifact at a time, not as a mass rewrite.

### Low-bureaucracy operation

The learner keeps one regular form: the daily log. Mentors and dispatchers generate petitions, dispatcher responses, and handover snapshots only when needed. The system must not spend more time on reporting than on learning.

## 11. Artifact register

Practical work is tracked by artifact IDs.

Allowed types:

| Type | Meaning |
|---|---|
| NOTE | Concept note, theory, explanation. A note alone does not produce mastery. |
| DRL | Drill, practicum, task or group of tasks. |
| UNT | Learning unit, especially Linux or English. |
| ADR | Project or architecture decision record. |
| EXM | Exam or transition check. |

Tests are not separate artifact types. They live inside `DRL`, `UNT`, or `EXM`.

## 12. The AI mentor

The system is designed to run with multiple AI chats.

Subject chats perform deep work: explanation, practice generation, checking, error analysis, and petitions.

The dispatcher performs system validation: it reads the daily log, checks petitions, confirms or rejects mastery, tracks debts, balance, sequence, current level, and process defects.

The mentor never writes the final solution. It asks questions, gives hints, and expects reconstruction. An AI that writes the solution for the learner breaks the system, because nothing is verified if nothing is reconstructed.

The mentor may generate correct AI variants when requested or when the source is unavailable. Such variants must match the source class, use only learned tools, be verifiable, and be marked as AI-generated when relevant. The source remains the arbiter.

## 13. The stack

Everything used in this project is open, free, or portable. Nothing requires a paid licence, a subscription, or a proprietary account to reproduce the method.

- Operating system — Linux.
- Editor — VS Code.
- Knowledge base — Obsidian, using Markdown and plain text.
- Version control — Git, with a public GitHub repository for the method and private repositories for project work.
- Language practice tools — free or open vocabulary and audio trainers.
- AI mentor — open-weight or free-tier large language models.

The choice is not ideological. Free, open, or portable tools reduce friction, keep the material portable, and remove the excuse that cost is a barrier.

## 14. Subject protocols

### Mathematics

Every problem passes through: given → model → tool → solution → check → restatement. The learner builds the model, not the mentor. Conditional structures such as state tables, motion diagrams, work tables, or graphs are used only when the problem class requires them. A Python mini-script is used when it meaningfully checks a formula or algorithm, not as a mandatory ritual for every micro-topic.

A Math `NOTE` explains meaning, method, boundaries, and typical errors. A Math `DRL` verifies independent solution, verification, and written explanation.

### Computer Science

Every concept is demonstrated by a mini-experiment when possible. The learner predicts the output before running it, compares prediction with actual output, explains the difference, and connects the concept to Python, Linux, or math.

A CS `NOTE` explains the concept and model. A CS `DRL` or `EXM` contains the experiment and evidence.

### Linux / command line

Every scenario is performed in a sandbox. The learner checks exit status, verifies results independently, and analyses at least one deliberate failure. Verification is not decoration: `ls`, `test`, `find`, and `echo $?` matter more than a pretty `tree`.

A Linux `NOTE` explains the system model, command anatomy, risks, and safety rules. A Linux `UNT`, `DRL`, or `EXM` contains the practical trace.

### Python

The learner predicts output before running code, writes code by hand, checks edge cases, applies PEP 8, and compares approaches when appropriate. The three-level method is bounded by the learner’s current Python level. A higher-level solution is not required before its tools have been learned.

A Python `NOTE` explains semantics and typical traps. A Python `DRL` or `EXM` verifies prediction, execution, edge cases, and written explanation.

### English

Grammar units cover form, meaning, usage, typical learner errors, and written practice. Sessions begin with a short warm-up recall. Speaking may be used as personal practice, but it is not a system requirement for mastery.

An English `NOTE` is an explanatory grammar map. It is not a worksheet and does not contain ready answers to Student’s Book, Workbook, or Murphy exercises. Exercises, tests, error correction, and written answers live in `UNT`, `DRL`, or `EXM`.

### Financial Navigator, short FinG

Phase 0 is a Python CLI project using JSON, files, functions, errors, and tests when the learner reaches the corresponding level. FinG has no knowledge map in Obsidian. Its roadmap lives in the private repository. FinG must not outrun the current Python level. Anything requiring classes, modules, databases, async, frameworks, Docker, or FastAPI belongs to the backlog. Mathematical metrics such as `L_norm`, floors, and amortization are implemented only after the corresponding Math topics are mastered.

FinG does not use petitions or `mastered` status. Its progress is visible through commits, roadmap updates, working code, and daily log lines.

## 15. Definition of done per phase

Phases are not passed by calendar. Each has explicit exit criteria — proven mastery in Python, Linux scenarios, mathematics, CS experiments, English, and a working Phase 0 FinG CLI.

Topics count only when confirmed as `mastered` in the knowledge maps. A phase closes through exam evidence, not calendar time.

For Phase 0, the learner must demonstrate:

- Python: confident solving of tasks on variables, conditions, loops, collections, functions, files, and errors.
- Linux: confident navigation, file operations, permissions, search, pipes, redirection, archives, and basic scripting.
- Mathematics: independent solution of typical school-algebra problems, with model building and verification.
- Computer Science: ability to demonstrate concepts through mini-experiments and explain machine behaviour.
- English: verified grammar and written practice for the active Phase 0 sources.
- FinG: a working Phase 0 CLI consistent with the learner’s current Python level.

## 16. Resource selection

One active source per subject at a time. It is replaced only when:

- the checklist of that source is fully `mastered`;
- at least two mini-exams on its topics have passed.

Before that, the source does not change — even if it gets boring. Switching mid-way is a hidden form of drift.

The mentor may generate AI variants when requested or when the source is unavailable, but such variants must match the source class, use only learned tools, be verifiable, and be marked as AI-generated when relevant. The source remains the arbiter.

All sources are open, free, or widely accessible. Which sources to use is part of the path. Each learner finds their own.