# zero-to-path

> This is a personal experiment: can a person starting from zero become an engineer through small, consistent steps?

[![License: MIT](https://img.shields.io/badge/License-MIT-blue?style=flat-square)](LICENSE)
[![Status](https://img.shields.io/badge/status-phase%200-brightgreen?style=flat-square)](#roadmap)
[![Last Updated](https://img.shields.io/badge/updated-2026--10--17-lightgrey?style=flat-square)](#current-progress)

---

## What this is

A public record of a long-term, self-directed engineering education — documented as a reproducible system rather than a diary.

The method is open. The journey is tracked.

The goal is to build a career from backend development into AI infrastructure, on a foundation of mathematics, computer science, Linux, and English. Not by heroic sprints, but by small, consistent steps measured over years.

## Why publish

If small steps work, this repository will show it. If they don't, it will show that too. Either outcome is worth documenting.

## How it works

Three pillars:

- **Knowledge maps** — one per subject. The single source of truth for topic status, and the hub that collects every note, drill, scenario, and practicum.
- **Mastery criteria** — a topic is only "mastered" after clean recall, a hands-on artifact, a solved set of typical problems, and a written explanation to the AI mentor.
- **Supporting discipline** — clean-sheet repetition, deliberate error labs, and spaced review at fixed intervals.

Full breakdown → [METHODOLOGY.md](METHODOLOGY.md)
Founding philosophy → [PHILOSOPHY.md](PHILOSOPHY.md)

---

## Roadmap

Four phases. The timeline is defined by mastery, not by calendar.

| Phase | Goal | Core stack | Status |
|---|---|---|---|
| **0 — Foundation** | Base in math, CS, language; first code | Python (basics), Linux CLI, school-level algebra, CS fundamentals, English A1→B1 | **← current** |
| **1 — Backend** | Junior Backend Developer | Python (OOP, FastAPI), PostgreSQL, SQL, Docker, REST | pending |
| **2 — Systems** | Professional backend, first C++ | C++ (memory, STL), linear algebra | pending |
| **3 — AI Infrastructure** | Engineer for AI systems | C++ (concurrency), CUDA/OpenCL, GPU architecture, pybind11 | pending |

---

## Current Progress

*Last updated: 2026-10-20*

| Subject                | Main resource                    | Progress                                              | Practicum                   |
| ---------------------- | -------------------------------- | ----------------------------------------------------- | --------------------------- |
| **Python**             | Stepik — Generation Python       | 389 / 2438                                            | Drill: branch classifier    |
| **Mathematics**        | Mordkovich, *Algebra 7*          | §5 tail                                               | Drill: alloys, 2 passed     |
| **Linux / Bash**       | Shotts, *The Linux Command Line* | Chapters 1–4                                          | Unit 2 — file operations    |
| **Computer Science**   | Bosova, *Informatics 6*          | 100 / 215                                             | Experiment: algorithm forms |
| **English — grammar**  | Murphy, *Grammar in Use*         | Unit 5                                                | Drill: U5 clean repeat      |
| **English — practice** | English File 4e Beginner         | Unit 2B                                               | Packet: 2B questions        |
| **Pet project**        | Phase 1 — Financial Navigator    | Repo initialized, Docs ready, Data models in progress | Python 3, CLI, JSON         |

*Full topic-level detail lives in the knowledge maps.*

---

## System structure

The repository is small: three public documents describing the method. The actual learning happens in a private Obsidian vault, organized like this:

```text
vault/
├── <subject>/               # Python, Math, Linux, CS, English
│   ├── <subject>_map.md     # source of truth: status, drills, risks
│   ├── Notes/               # concept notes linked to the map
│   ├── Tests/               # drill scenarios and clean-repeat artifacts
│   └── Resources/           # reference material (not an active track)
├── Daily/                   # daily logs and reflections
├── Projects/                # pet projects per phase
└── Inbox/                   # incoming, unsorted
```

Each subject has exactly one map. Notes without a map do not exist.

Public files: `README.md`, `PHILOSOPHY.md`, `METHODOLOGY.md`, plus `code/`, `templates/`, `docs/` for future artifacts.

---

## Tooling

- **OS:** Linux (Ubuntu)
- **Editor:** VS Code
- **Knowledge base:** Obsidian
- **Version control:** Git + GitHub
- **AI mentor:** open-weight or free-tier large language models

All tools are open-source, free, or both. Nothing requires a paid licence to reproduce.

---

## License

[MIT](LICENSE)