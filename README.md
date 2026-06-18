# Teller

A file-based story bible framework for AI-assisted fiction writing. Any AI with file access can navigate it with precision — no memory, no plugins, no special setup.

---

## What it is

A directory of `.md` files with YAML frontmatter. Each file (a **Node**) declares its own dependencies via a `load-with` field. When an AI loads a character node, it knows exactly which system, world, and voice files to also load — no guessing, no noise.

The result: consistent, canon-accurate writing assistance across sessions, projects, and models.

---

## Core concepts

| Term | What it is |
|---|---|
| **Node** | Atomic `.md` file with YAML frontmatter. One concept per file. |
| **Module** | Category folder (`characters/`, `world/`, `system/`, `plot/`, etc.) |
| **Bundle** | Predefined node set for a specific task (`write/`, `continuity-check`, `session-close`) |
| **load-with** | Frontmatter field — node declares its own dependencies. The key to precision. |
| **state.md** | Per-project file tracking current position, last chapter written, next chapter plan. |

---

## How to use it

### Requirements

- [Claude Code](https://claude.ai/code) (CLI or desktop app)
- This repo cloned locally

### Start a session

```bash
cd path/to/Teller
claude
```

Claude Code reads `CLAUDE.md` automatically. It scans `projects/`, reads the active project's `state.md`, and outputs an unprompted welcome block:

- Project table — each project with active book and status
- Command reference — what you can ask and how
- Active project orientation — current position + open threads

### Actions

| Action | How to ask |
|---|---|
| Write a chapter | `escribe el cap X` |
| Plan | `planifiquemos el cap X` / `el arco X` / `el Libro X` |
| Edit existing chapter | `edita el cap X` |
| Continuity check | `verifica continuidad del cap X` |
| End session | `/session-close X` |
| New book, same universe | `/new-book N` |
| New project | `/new-project [nombre]` |

**Planning detects granularity automatically** — cap, batch, arc, book, or scene/event. No separate commands needed.

**Editing a past chapter** doesn't touch `state.md` or progression — only updates `chapters/index.md` if the summary changed.

### End of session

```
/session-close 38
```

Protocol:
1. Checks continuity flags (blocks if unresolved)
2. Proposes updated `state.md`
3. Proposes new row in `chapters/index.md`
4. Offers `update-nodes` canon diff
5. If final chapter: prompts to mark book complete → surfaces `/new-book` or `/new-project`

Nothing applied without confirmation at each step.

### New book, same universe

```
/new-book 2
```

Shared nodes: world, system, characters. Versioned by book:

- `voice/style.md` — adds `## Book 2` section (Book 1 preserved)
- `themes/writing-rules.md` — adds `## Book 2` section
- `plot/arcs-book2.md` — new arc structure file

Updates `state.md → active-book: 2` and `CLAUDE.md → Active book: 2`.

---

## Starting a new project

Two triggers:

**Slash command:**
```
/new-project [working-title]
```

**Natural phrase** — Claude detects and confirms:
```
quiero empezar un libro
nueva historia
tengo una idea para una novela
```

Both run the same structured intake (6 steps). Claude asks for the exact fields each node template requires. Say "TBD" for anything unknown — filled with `<!-- TBD -->` and revisited later.

**Parse mode:** if you arrive with narrative ideas already formed, Claude extracts what it can from your description and only asks for missing fields.

**Intake order:**
1. Project meta → `index.md`
2. Protagonist → `characters/[id].md`
3. Setting → `world/[id].md`
4. Voice → `voice/style.md`
5. Plot skeleton → `plot/arcs.md`

After step 5: folders scaffolded, `CLAUDE.md` updated, ready to plan cap 1.

---

## File structure

```
Teller/
├── CLAUDE.md                  ← Claude Code reads this automatically on session start
├── AGENTS.md                  ← Agent spec
├── manifest.md                ← System entry point — terminology definitions
├── routes.md                  ← Full path map
├── bundles/
│   ├── develop.md             ← New project intake protocol
│   ├── continuity-check.md
│   ├── update-nodes.md
│   ├── session-close.md
│   └── write/
│       ├── index.md
│       ├── dialogue.md
│       ├── action.md
│       └── introspection.md
├── .claude/
│   └── commands/
│       ├── session-close.md   ← /session-close
│       ├── new-project.md     ← /new-project
│       └── new-book.md        ← /new-book
├── _planning/                 ← Planning content, not loaded during writing
├── _templates/                ← Node templates
└── projects/
    └── [project-name]/
        ├── state.md           ← Current position, next chapter, open threads
        ├── characters/
        ├── voice/             ← style.md + pov-[id].md per POV character
        ├── system/
        ├── world/
        ├── plot/
        ├── relations/
        ├── bestiary/
        ├── themes/
        └── chapters/          ← Navigation index to manuscript files
```

---

## Publishing

Manuscript files are Markdown.

- **Royal Road:** `pandoc chapter.md -o chapter.html` → paste HTML into chapter editor (source mode)
- **Wattpad:** paste Markdown directly — basic formatting renders natively

---

## Session workflow

```
open Claude Code in Teller/
        ↓
Claude reads CLAUDE.md → scans projects/ → reads active state.md
        ↓
welcome block: project table + command guide + orientation
        ↓
write / plan / edit / continuity check
        ↓
chapter complete → Claude suggests /session-close
        ↓
/session-close → state.md + chapters/index.md updated
        ↓
if final chapter → /new-book or /new-project suggestion
        ↓
next session starts oriented
```
