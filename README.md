[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

# Obsidian Vault Template
Reusable Obsidian vault skeleton for Personal-OS: tasks, calendar, projects, areas, and daily notes - built on a 3-layer architecture (raw/ -> wiki/ -> archive/) with Task status enum (`status:` field on each task; folder mirrors status).

- **`raw/`** — immutable inbox, two sub-layers: root = uncategorized drop zone; subfolders = categorized (`captures/` + `external/` required, `emails/` opt-in). Never edit after writing.
- **`wiki/`** — linked data network (the work surface; edited and re-edited)
- **`meta`** — `AGENTS.md` + `index.md` + `log.md` (conventions + map + history)

## Features

- **5 community plugins pre-configured**: Templater, Dataview, obsidian-tasks, QuickAdd, Calendar (liamcain)
- **7 templates** (in `templates/`): `area`, `capture`, `daily`, `event`, `project`, `recurring-event`, `task`
- **Folder skeleton** for tasks / calendar / projects / areas / daily / archives
- **Task status** enum (`status:` field) — each task has inbox / next / waiting / someday / done / cancelled; folder mirrors status
- **Commit convention**: `YYYY-MM-DD <type> | <description>`
- **Capture traces** in `raw/captures/` for full provenance of every wiki page

## Quick Start

```bash
git clone <this-repo> ~/my-vault
cd ~/my-vault
# In Obsidian: "Open folder as vault" → pick ~/my-vault
# Reload Obsidian to activate community plugins
```

On first launch, Obsidian will download plugin code from its registry (only `data.json` is committed here).

## Folder Structure

```
.
├── AGENTS.md            ← operations manual (read first)
├── README.md            ← this file
├── index.md             ← vault contents index (wikilinks only)
├── log.md               ← operation log (append-only)
├── .gitignore           ← ignores workspace.json, cache, trash
├── .obsidian/           ← Obsidian config (plugins, app settings)
│   ├── app.json         ← dailyNotesFolder, templates folder
│   ├── community-plugins.json
│   ├── core-plugins.json
│   └── plugins/{templater,dataview,obsidian-tasks,quickadd,calendar}/data.json
├── templates/           ← 7 Templater templates
│   ├── area.md
│   ├── capture.md
│   ├── daily.md
│   ├── event.md
│   ├── project.md
│   ├── recurring-event.md
│   └── task.md
├── raw/                 ← immutable, two sub-layers
│   ├── <root>           ← Layer 1: uncategorized drop zone (triage target)
│   ├── captures/        ← Layer 2a: your time-stamped records (YYYY-MM-DD-*.md) — REQUIRED
│   ├── external/        ← Layer 2b: third-party sources (web clips, papers, lecture notes) — REQUIRED
│   └── emails/          ← Layer 2c: email (inbound + outbound, including AI drafts) — OPT-IN
└── wiki/                ← editable, source of work
    ├── tasks/           ← task state machine (status: enum; folder mirrors status)
    │   ├── inbox/       ← untriaged captures from raw/captures/
    │   ├── next/        ← active tasks
    │   ├── waiting/     ← blocked-on tasks
    │   ├── someday/     ← maybe-later tasks
    │   └── done/        ← completed tasks (archive; archive >10/month → done/YYYY-MM/)
    ├── calendar/
    │   ├── daily/       ← per-day recurring event instances
    │   ├── recurring/   ← recurring event templates
    │   └── synced/      ← from external calendar sync
    ├── projects/        ← one folder per project
    ├── areas/           ← ongoing responsibilities
    ├── daily/           ← daily notes (YYYY-MM-DD.md)
    └── archives/
        ├── projects/     ← closed projects
        └── tasks/       ← old done tasks (moved out of done/)
```

## Task status (enum)

Every task has a `status:` field (required). Folder mirrors status.

| Status | Folder | Notes |
|---|---|---|
| `inbox` | `wiki/tasks/inbox/` | Triaged, not yet scheduled |
| `next` | `wiki/tasks/next/` | Active this week |
| `waiting` | `wiki/tasks/waiting/` | Blocked on someone/something |
| `someday` | `wiki/tasks/someday/` | Maybe later |
| `done` | `wiki/tasks/done/YYYY-MM/` | Completed (set `completed:` date) |
| `cancelled` | `archives/tasks/` | Will not do |

Captures in `raw/captures/` are pre-task. Use `triaged:` + `triage_target:` for status tracking.


## Commit Convention

Format: `YYYY-MM-DD <type> | <description>`

Types: `docs`, `test`, `schema`, `init`, `dashboard`, `sim`, `plugins`, `task`, `area`, `project`, `cleanup`, `fix`, `restructure`, `ingest`, `lesson`, `comparison`, `overview`, `area`, `capture`.

## What's NOT included (you provide)

- `wiki/daily/*.md` — your daily notes (created on demand)
- `wiki/tasks/next/*.md` — your tasks
- `wiki/areas/*.md` — your areas
- `raw/captures/*.md` — your source captures
- `dashboard/` — your home dashboard (if any)
- `.obsidian/workspace.json` — Obsidian window layout (per-machine)

## License
## Adapting this template

Fork / clone freely. When forking:

1. Update vault name in prose
2. Add your first task via Ctrl+P -> QuickAdd -> Task
3. Open wiki/daily/today.md

## Related project: LLM-Wiki

A separate companion vault (LLM-Wiki/) uses the same skeleton adapted for knowledge-base work
(entities, concepts, comparisons, summaries, lessons) -
following the Karpathy LLM Wiki pattern.
Personal-OS is for doing; LLM-Wiki is for learning.

## License

MIT License — Copyright © 2026 me9487ab-commits. See [LICENSE](LICENSE) for the full text.