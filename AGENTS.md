<!--
📦 TEMPLATE-NOTE
This file is the operations manual for the vault-template repo. It covers
Personal-OS mode (tasks / calendar / projects / areas / daily) plus the
shared architecture (3-layer model, task status enum, raw/ two-layer, SOPs).

When forking this repo for a new vault:
1. Rename the wiki/ subfolders to fit your taxonomy
2. Replace template names with your vault name in any prose
3. Update the "What YOU provide" section to match what data you will keep
4. Delete this banner block once adapted
-->

---
date: 2026-10-02
type: meta
tags: [schema, operations-manual]
status: active
---

# AGENTS.md — Operations Manual

> **TL;DR** — Drop uncategorized stuff in `raw/` root, triage to `raw/<sub>/`. Work lives in `wiki/`. Use status: enum (see § Task status). Commit format: `YYYY-MM-DD <type> | <description>`.

---

## Pick your mode (do this first)

This template ships with Personal-OS scaffolding but the same skeleton supports **three modes**. Choose based on what your vault is for:

| Mode | Best for | `wiki/` subfolders |
|---|---|---|
| **Personal-OS** (productivity) | GTD, calendar, areas, projects, daily notes | `tasks/{inbox,next,waiting,someday,done}/`, `calendar/{daily,recurring,synced}/`, `projects/`, `areas/`, `daily/`, `archives/{projects,tasks}/` |

---

## The 3-layer model (every mode)

```
Layer 1  raw/        immutable inbox. Agents read; never edit.
Layer 2  wiki/       work surface. Edit, evolve, wikilink.
Layer 3  meta        AGENTS.md + index.md + log.md (schema, map, history)
```

| Layer | What lives here | Rule |
|---|---|---|
| `raw/` | Your captures + external third-party sources (both required) + emails (opt-in) | **Two sub-layers**: root = uncategorized buffer, subfolders = categorized. `raw/captures/` and `raw/external/` are created by default; `raw/emails/` is opt-in. See § raw/ two-layer model below. |
| `wiki/` | Tasks, events, projects, areas, daily notes, summaries, entities, concepts | Edit freely. Use wikilinks. Use status: enum (see § Task status). |
| meta | `AGENTS.md` (this file), `index.md` (map), `log.md` (history) | `index.md` = wikilinks-only, never describe. `log.md` = append-only. |

---

## raw/ two-layer model

The `raw/` layer itself splits into two:

| Sub-layer | Location | Purpose |
|---|---|---|
| **Layer 1 — uncategorized** | `raw/` root (e.g. `raw/2026-10-02-meeting-thought.md`) | Quick-drop buffer. No `type:` required. Triage target. |
| **Layer 2 — categorized** | `raw/<sub>/` subfolders | Post-triage home. Organized by source type. |

### The categorized subfolders (1 required + 2 opt-in)

| Subfolder | Holds | Naming convention | Required? |
|---|---|---|---|
| `raw/captures/` | Your own time-stamped records: voice notes, screenshots, reflections, meeting minutes | `YYYY-MM-DD-<slug>.md` | ✅ Required |
| `raw/external/` | Third-party sources ingested for reading: web clips, book chapters, lecture handouts, PDFs → markdown | `<source-slug>.md` (often includes source identifier, e.g. `fluid-mech-2026-09-30-handout.md`) | ✅ Required |
| `raw/emails/` | Email correspondence, both inbound and outbound (including AI-drafted replies) | `YYYY-MM-DD-<subject-or-sender>.md` | ⭕ Opt-in |

`raw/captures/` and `raw/external/` are created by default. Enable `raw/emails/` only if your workflow needs it:

```bash
# Enable email flow
mkdir -p raw/emails && touch raw/emails/.gitkeep
```

To disable an opt-in folder: just delete it. No migration needed — the workflows reference it only when it exists.

To disable any opt-in folder: just delete it. No migration needed — the workflows reference these folders only when they exist.

### Triage flow

1. **Drop** anything into `raw/` root first — no classification needed (e.g. `raw/2026-10-02-something.md`)
2. **Triage** daily (or as needed): move the file into the matching subfolder and rename to convention if needed
3. **Add provenance**: when the file is consumed into a wiki page, link via frontmatter `source: raw/...`

### Rules

- ❌ Never leave files in `raw/` root indefinitely — backlog kills the buffer
- ❌ Never edit a raw/ file once written (append a new capture instead)
- ❌ Don't reference `raw/emails/` path unless you created it (it's opt-in)
- ✅ When unsure which subfolder fits, leave in root and decide next triage
- ✅ Filenames in root can be informal — rename when triaged
- ✅ `raw/emails/` is truly optional — delete if you don't need it

---

## Task status (enum)

Every task in wiki/tasks/** has a status: field (required). The folder the file lives in should match its status.

| Status | Folder | Notes |
|---|---|---|
| inbox | wiki/tasks/inbox/ | Triaged, not yet scheduled |
| next | wiki/tasks/next/ | Active this week |
| waiting | wiki/tasks/waiting/ | Blocked on someone/something |
| someday | wiki/tasks/someday/ | Maybe later |
| done | wiki/tasks/done/YYYY-MM/ | Completed (set completed: date) |
| cancelled | archives/tasks/ | Will not do |
| recurring | wiki/calendar/recurring/ | Habits / routines (NOT a task). Tracked via daily notes. |

Captures in raw/captures/ are pre-task. Use triaged: + triage_target: for status tracking.

---

## Workflow — Personal-OS mode

#### 1. Capture

New stuff always goes to `raw/` first (root or subfolder, see § raw/ two-layer model).

- Voice-to-text notes, quick thoughts, screenshots → `raw/` root (triage later) or straight to `raw/captures/`
- Web clipper outputs, book/PDF highlights, lecture notes → `raw/external/`
- AI-written email reply drafts → `raw/emails/` *(if that opt-in folder exists)*

**Rule: capture without classification. Triage later.** If a target subfolder doesn't exist (e.g. `raw/emails/` not enabled), leave the file in `raw/` root until you decide.

**Recurring rules** belong in `wiki/calendar/recurring/` (not `raw/`). When
defining a new habit, capture it straight there with `type: recurring`
frontmatter; do not write a one-off task for each occurrence.

#### 2. Triage

Daily (or as needed): move things from `raw/` root to their right home.

- Is a task? → `wiki/tasks/inbox/` (or straight to `next/` / `waiting/` / `someday/`)
- Is a calendar event? → `wiki/calendar/synced/` (one-time) or `wiki/calendar/recurring/` (recurring)
- Is a project? → `wiki/projects/<project-slug>/`
- Is an ongoing responsibility? → append to `wiki/areas/<area>.md`


When triaging, add `source: raw/captures/<filename>` to frontmatter for provenance.

#### 3. Daily brief

Open `wiki/daily/YYYY-MM-DD.md` each morning. Templater + Dataview auto-pull:

- Today's tasks (from `wiki/tasks/next/`)
- Overdue tasks
- This-week deadlines
- Active project names
- Today's calendar events

#### 4. Review cadence

| Frequency | Action |
|---|---|
| Daily | Clear `tasks/inbox/`, write daily reflection |
| Weekly | Review `tasks/next/` + `tasks/waiting/`, verify `calendar/recurring/` |
| Monthly | Move old `tasks/done/` → `archives/tasks/`, review all `projects/` status |
| Quarterly | Review all `areas/`, confirm each has recent focus |

### 5. Recurring habits

Some obligations repeat on a schedule but are **not tasks** — they are habits
(routine behaviors that sustain you). Track them in `wiki/calendar/recurring/`
(e.g. `habits.md`), not in `wiki/tasks/`.

**Difference from a task:**
- A task has a clear "done" moment (commit, deliverable, decision).
- A habit is a recurring behavior with no single completion (e.g. take
  supplements, exercise, journal).

**How to track:**

1. **Define the rule** in `wiki/calendar/recurring/<topic>.md` with frontmatter:
   `type: recurring`, `title:`, `frequency:` (`daily` / `every-N-days` /
   `weekdays` / `Mon,Wed,Fri`), `check-state:`, `reminder:`.
2. **Surface in daily notes** (`wiki/daily/YYYY-MM-DD.md`) via
   `## Recurring` section auto-generated from habit files.
3. **Status updates**: agent runs SOP-Daily-Brief each morning; user
   confirms with "吃了 / 去了 / done" replies.

**Rules:**
- ❌ Do NOT create habit files in `wiki/tasks/` — habits have no single
  "done" event.
- ❌ Do NOT use `recurring-event` type for habits — that is for scheduled
  appointments with a fixed time (e.g. doctor visit every Tuesday 10am).
- ✅ One habit file per topic (e.g. `habits.md`, `exercise.md`).
- ✅ Pause a habit by setting `status: paused` (agent skips paused habits).
- ✅ When a habit becomes a project, migrate to `wiki/projects/<project>/`
  and link back to the habit file.

For detailed algorithms (every-N-days math, supplement 2x/day prompting,
daily-note generation), see `wiki/calendar/recurring/README.md`.

---

## Naming conventions

| Item | Convention | Example |
|---|---|---|
| Folders, files | lowercase + dash | `engineering-mechanics-3/` |
| Dates | ISO 8601 (`YYYY-MM-DD`) | `2026-10-02.md` |
| Times in filenames | `HH-MM` (24h, dash not colon — colon breaks some filesystems) | `2026-10-02-09-30-meeting.md` |
| Slugs | dash-separated keywords | `cs-team-meeting` |
| Completed tasks archive | `wiki/tasks/done/YYYY-MM/` | `wiki/tasks/done/2026-10/...` |

| raw/ root files (informal) | descriptive slug | `meeting-thoughts.md` |
| `raw/captures/` | `YYYY-MM-DD-<slug>.md` | `2026-10-02-think-pomodoro.md` |
| `raw/external/` | `<source-slug>.md` (date optional) | `fluid-mech-2026-09-30-handout.md` |
| `raw/emails/` *(opt-in)* | `YYYY-MM-DD-<subject-or-sender>.md` | `2026-10-02-reply-to-bill.md` |

---

## Frontmatter conventions

#### Personal-OS mode

| Type | Required fields | Template |
|---|---|---|
| task | `date`, `type: task`, optional `project:`, `area:` | `templates/task.md` |
| project | `type: project`, `status:`, `area:` | `templates/project.md` |
| area | `type: area`, `status:` | `templates/area.md` |
| daily | `date`, `type: daily` | `templates/daily.md` |
| capture | `date`, `type: capture`, `source:` | `templates/capture.md` |
| event | `date`, `type: event`, `title`, `start`, `end` | `templates/event.md` |
| recurring-event | `type: recurring-event`, `title`, `start-time`, `duration`, `days`, `start-date` | `templates/recurring-event.md` |

---

## Wikilink style

- **Basename only**: `[[page-name]]` — never `[[wiki/summaries/foo]]`
- **Cross-folder**: `[[folder/page|Display Text]]` (only when needed)
- **Tasks ↔ projects/areas**: use frontmatter fields, not wikilinks (so Dataview can query)
- **Graph View**: shows the network — let it surprise you

If a wikilink target doesn't exist, it shows as broken (red). Lint pass should fix these.

---

## Commit convention

```
YYYY-MM-DD <type> | <description>
```

Common types:

| Type | Use for |
|---|---|
| `docs` | Documentation, READMEs, AGENTS.md changes |
| `init` | Initial commit / scaffold |
| `schema` | Frontmatter or folder schema changes |
| `task` | New task / task update |
| `area` | New area / area update |
| `project` | New project / project update |
| `event` | Calendar event |
`cleanup` | Delete / archive / reorganize |
| `fix` | Bug fix, broken link, typo |
| `restructure` | Folder restructure |
| `plugins` | Plugin install / config / remove |
| `dashboard` | Dashboard layout / Dataview query |
| `sim` | Simulation run |

Commit body (after the title) should explain *why*, not restate *what*. 2-5 lines.

---

## What's excluded (YOU provide)

These are intentionally not in the template — your vault needs its own:

- `wiki/daily/YYYY-MM-DD.md` — your daily notes
- `wiki/tasks/next/*.md` — your active tasks
- `wiki/areas/*.md` — your areas of responsibility
- `wiki/projects/*/` — your projects
- `raw/captures/*.md` — your source captures
- `dashboard/` — your home dashboard (if any)
- `.obsidian/workspace.json` — Obsidian window layout (per-machine)
- `.obsidian/appearance.json` — your theme preferences

The skeleton gives you **shape**, you give it **life**.

---

## Adapting to your use

#### If forking for Personal-OS (Mode A):

Default state. Just delete the TEMPLATE banner.

#### If forking for Hybrid (Mode C):

Fork the repo twice — one as Mode A, one as Mode B. Use wikilinks (e.g. `[[other-vault:concept-name]]`) to cross-reference between them.

---

## Provenance (capture trace)

For every wiki page that came from a source, the trail should be:

```
raw/<source>.md  ──────┐
                       │  produced these wiki pages:
raw/captures/<date>-<slug>.md  (the "trace" — points to:)
                       ↓
              ┌────────┼────────┬────────┬────────┐
              ↓        ↓        ↓        ↓        ↓
         summary.md entity.md concept.md  ...    ...
```

The capture file in `raw/captures/` records which wiki pages were produced from which source. This is the source of truth for "where did this page come from?".

---

## Prohibited (across all modes)

- ❌ Edit files inside `raw/` once written (append a new capture instead)
- ❌ Skip frontmatter on any wiki page
- ❌ Mix uppercase / lowercase / camelCase in filenames
- ❌ Use `[[wiki/...]]` path-based wikilinks (use `[[basename]]`)
- ❌ Skip `log.md` updates — append-only, never rewrite
- ❌ Put book notes / study notes / topic wiki into this vault — knowledge work is not in Personal-OS scope
- ❌ Add a status: field that contradicts folder location (e.g. status: next in inbox/)
- ❌ Leave `raw/` root backlog unprocessed for long periods (defeats the uncategorized buffer purpose)

- ❌ Track habits as tasks in `wiki/tasks/` — habits are not deliverables;
  use `wiki/calendar/recurring/` + daily note checkboxes instead.

---

## License

MIT License — Copyright © 2026 me9487ab-commits. See [LICENSE](LICENSE) for the full text.