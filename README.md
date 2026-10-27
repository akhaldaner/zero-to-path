# zero-to-path

This is a personal experiment: can a person starting from zero become an engineer through small, consistent steps?

![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)
![Status](https://img.shields.io/badge/status-phase%200-brightgreen?style=flat-square)
![Updated](https://img.shields.io/badge/updated-2026--10--28-lightgrey?style=flat-square)
![System](https://img.shields.io/badge/system-Reloaded%20v1-blue?style=flat-square)

## What this is

A public record of a long-term, self-directed engineering education — documented as a reproducible system rather than a diary.

The method is open. The journey is tracked.

The goal is to build a career from backend development into AI infrastructure, on a foundation of mathematics, computer science, Linux, and English. Not by heroic sprints, but by small, consistent steps measured over years.

This repository describes the public method. The learning vault, private notes, and project code live outside it.

## Why publish

If small steps work, this repository will show it. If they don't, it will show that too. Either outcome is worth documenting.

## How it works

Four pillars:

1. Knowledge maps — one per subject. The single source of truth for topic status.
2. Artifact IDs — stable identifiers for notes, drills, units, decisions, and exams.
3. Petition-based mastery — subject mentors propose `mastered`; dispatchers confirm it.
4. Low-bureaucracy operation — the learner keeps one daily log; AI generates petitions, dispatcher responses, and handover state.

Full breakdown → [METHODOLOGY.md](METHODOLOGY.md)

Founding philosophy → [PHILOSOPHY.md](PHILOSOPHY.md)

## Roadmap

Four phases. The timeline is defined by mastery, not by calendar.

| Phase | Goal | Core stack | Status |
|---|---|---|---|
| 0 — Foundation | Base in math, CS, language; first code | Python basics, Linux CLI, school-level algebra, CS fundamentals, English A1→B1 | ← current |
| 1 — Backend | Junior Backend Developer | Python OOP, FastAPI, PostgreSQL, SQL, Docker, REST | pending |
| 2 — Systems | Professional backend, first C++ | C++ memory, STL, linear algebra | pending |
| 3 — AI Infrastructure | Engineer for AI systems | C++ concurrency, CUDA/OpenCL, GPU architecture, pybind11 | pending |

## Current Progress

Last updated: 2026-10-28.

This is an operational snapshot. Knowledge maps are the source of truth.

| Subject            | Active source                               | Current focus                                   | Operational state |
| ------------------ | ------------------------------------------- | ----------------------------------------------- | ----------------- |
| Python             | Stepik — Generation Python                  | 4.3 nested/cascaded conditions, elif            | in_progress       |
| Mathematics        | Mordkovich, Algebra 7                       | §5 percents, alloys, ores; examples 9–13        | in_progress       |
| Linux / Bash       | Shotts, The Linux Command Line + SadServers | Unit 2 file operations and wildcards; tasks 7–8 | debt              |
| Computer Science   | Bosova, Informatics 6                       | §14 algorithms                                  | in_progress       |
| English — grammar  | Murphy, Essential Grammar in Use            | Unit 5 migration candidate                      | pending migration |
| English — practice | English File 4e Beginner                    | Unit 2B WH-questions with be                    | debt              |
| Pet project        | Financial Navigator, short FinG             | Phase 0 CLI, private repo, roadmap in repo      | in_progress       |

## System structure

The public repository contains the method. The private Obsidian vault contains the learning artifacts.

Each subject follows the same pattern:

```text
<Subject>/
├── <subject>_map_of_content.md
├── Notes/
├── Tests/ or Tasks/
└── Resources/
```

The actual vault is organized as follows:

```text
vault/
├── Math/
│   ├── Math_map_of_content.md
│   ├── Notes/
│   ├── Tasks/
│   └── Resources/
├── Python/
│   ├── Python_map_of_content.md
│   ├── Notes/
│   ├── Tests/
│   ├── Resources/
│   └── Projects/
│       └── FinG/
├── Linux/
│   ├── Linux_map_of_content.md
│   ├── Notes/
│   ├── Tests/
│   └── Resources/
├── English/
│   ├── English_map_of_content.md
│   ├── Notes/
│   ├── Tests/
│   ├── Murphy_Grammar_in_Use/
│   ├── English_File/
│   └── Resources/
├── CS/
│   ├── CS_map_of_content.md
│   ├── Notes/
│   ├── Tests/
│   └── Resources/
├── Daily/
│   ├── dispatcher_state.md
│   ├── Logs/
│   └── Templates/
├── GitHub/
│   └── zero-to-path/
└── Inbox/
```

Each subject has exactly one map. Notes without a map do not exist in the active system.
## Public files

- `README.md`
- `PHILOSOPHY.md`
- `METHODOLOGY.md`
- `code/`
- `templates/`
- `docs/`

The method repository is public. The learning vault is private. The FinG project repository is private during Phase 0. Public progress is represented by method documents, selected code samples, and non-sensitive artifacts.

## Tooling

- OS: Linux
- Editor: VS Code
- Knowledge base: Obsidian
- Version control: Git + GitHub
- Method repository: public `zero-to-path`
- Project repository: private `FinG`
- AI mentor: multi-chat subject mentors plus dispatcher
- Handover state: `Daily/Dispatcher_state.md`

All tools are open-source, free, or portable. Nothing requires a paid licence to reproduce the method.

## License

[MIT](LICENSE)