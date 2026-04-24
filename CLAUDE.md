# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

An Obsidian vault containing a 16-week periodised parkour conditioning programme. There is no build system, no tests, and no runnable code. All content is Markdown with YAML frontmatter, rendered and navigated via Obsidian.

## Vault structure

- `_hub.md` — entry point; Dataview progress tables + phase map with wikilinks
- `parkour-trainer.md` — programme overview with links to all phases
- `phase-{n}-*.md` — one note per phase (1–6), each containing all sessions with exercises, cues, and embedded video
- `templates/session-log.md` — Templater template; users fill this in and save under `sessions/`
- `sessions/` — user-created session log notes (not in the repo initially)

## Frontmatter conventions

| File type | `type` value | Key fields |
|-----------|-------------|------------|
| Hub | `hub` | — |
| Overview | `overview` | — |
| Phase notes | `parkour-phase` | `phase` (1–6), `name`, `weeks`, `unlock_criteria`, `goal` |
| Session logs | `parkour-session` | `date` (YYYY-MM-DD), `phase`, `week`, `session`, `feel` (1–5) |

## Phase structure and gating

| Phase | Weeks | Unlock condition |
|-------|-------|-----------------|
| 1 Foundation | 1–2 | Starting phase |
| 2 Static Strength | 3–4 | All 6 Phase 1 sessions complete |
| 3 Dynamic Strength | 5–6 | 15 push-ups + wall sit 60s |
| 4 Explosive Power | 7–8 | Nordic curl 80% depth · stick landing 4/5 · dead hang 40s |
| 5 Body Control | 9–12 | Silent depth drop · explosive push-up hands airborne · reactive circuit quality stable |
| 6 Pre-Parkour Integration | 13–16 | Full Phase 5 assessment passed |

## Exercise logging types

Each exercise specifies one of three log types: `Quality` (1–5), `Time` (seconds), or `Reps`. Keep this consistent when editing phase notes.

## Graph navigation (backlinks)

Each phase note links to its neighbours with `[[wikilink]]` syntax, forming a chain in the graph view:

```
parkour-trainer → Phase 1 ↔ Phase 2 ↔ Phase 3 ↔ Phase 4 ↔ Phase 5 ↔ Phase 6
                               ↑           ↑
                            (all linked to _hub)
```

Session log notes gain a graph edge to their phase note via the `[[phase-N-name]]` wikilink that users place in the body when filling out the template.

Cross-phase references (e.g., Phase 3 referencing Phase 2's Nordic curl setup) also use `[[]]` wikilinks to build richer graph connections.

## YouTube embed syntax

Videos are embedded using Obsidian's native syntax — an image link with a YouTube URL renders as an inline player in Reading View:

```
![](https://www.youtube.com/watch?v=VIDEO_ID)
```

Do not use `[text](url)` hyperlink format for videos — it creates a link, not an embed.

## Session logging approach

- **Frontmatter** (`date`, `phase`, `week`, `session`, `feel`): queried by Dataview in `_hub.md` for the progress tables
- **Inline Dataview field** `[feel:: ]` in the note body: available for direct Dataview inline queries
- **`[key_result:: ]`** field: the standout metric for the session (a number, time, or quality score)
- Benchmark exercise results go in the exercise table in the session body

## Dataview path

Session logs are stored at `sessions/` from the vault root. The Dataview queries in `_hub.md` use `FROM "sessions"`. If this vault is opened as a subfolder of a larger vault, this path must be updated to match.

## Obsidian plugins relied on

- **Dataview** — powers progress tables in `_hub.md`; requires `type: parkour-session` frontmatter in session logs
- **Templater** — `templates/session-log.md` uses `<% tp.date.now("YYYY-MM-DD") %>` syntax; do not replace with plain text
