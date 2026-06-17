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

Claude Code reads `CLAUDE.md` automatically. It then reads `manifest.md` and the active project's `state.md`, and gives you an unprompted orientation: where the story is, what comes next, open threads.

If it doesn't orient on the first turn:

```
lee manifest.md y state.md
```

### Write a chapter

```
escribe el cap 38
```

Claude loads `bundles/write/` → infers dialogue / action / introspection → loads `voice/style.md` + `themes/writing-rules.md` + character nodes for the scene → each character node pulls its own POV file and system nodes via `load-with`.

Output: Markdown draft. Ambiguous canon marked with `<!-- OPEN: [question] -->`.

### Plan a chapter

```
planifiquemos el cap 38
```

Claude loads `plot/arcs.md` + `state.md` + `relations/conflicts.md` → produces a beat sheet.

### Continuity check

```
verifica continuidad del cap 37
```

Claude loads `bundles/continuity-check.md` → reports contradictions only. No rewrites.

### End of session

```
/session-close 38
```

Step-by-step protocol:
1. Checks for unresolved continuity flags (blocks if any)
2. Proposes updated `state.md` — where you are now, what comes next
3. Proposes new row in `chapters/index.md`
4. Offers to run `update-nodes` to propose canon diffs

Nothing is applied without your confirmation at each step.

---

## File structure

```
Teller/
├── CLAUDE.md                  ← Claude Code reads this automatically on session start
├── AGENTS.md                  ← Agent spec (for building automation on top)
├── manifest.md                ← System entry point — defines all terminology
├── routes.md                  ← Full path map
├── bundles/
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
│       └── session-close.md   ← /session-close slash command
├── _planning/                 ← Planning-only content, not loaded during writing
├── _templates/                ← Node templates
└── projects/
    └── [project-name]/
        ├── state.md           ← Current position, next chapter, open threads
        ├── characters/        ← One node per character
        ├── voice/             ← style.md + pov-[id].md per POV character
        ├── system/            ← Domain mechanics
        ├── world/             ← Settings, institutions, metaphysics
        ├── plot/              ← Arcs, timeline, key documents
        ├── relations/         ← Relationship webs, open conflicts
        ├── bestiary/          ← Threats and entities
        ├── themes/            ← Writing rules and constraints
        └── chapters/          ← Navigation index to manuscript files
```

---

## Adding a new project

1. Copy `_templates/` structure into `projects/[new-project]/`
2. Update `CLAUDE.md` — change `Active project:` to the new project name
3. Fill `state.md` with current position
4. Start writing

---

## Publishing

Manuscript files are Markdown. To publish:

- **Royal Road:** `pandoc chapter.md -o chapter.html` → paste HTML into chapter editor (source mode)
- **Wattpad:** paste Markdown text directly — basic formatting renders natively

---

## Session workflow summary

```
open Claude Code in Teller/
        ↓
Claude reads CLAUDE.md → manifest.md → state.md
        ↓
orientation (unprompted)
        ↓
write / plan / continuity check
        ↓
chapter complete → Claude suggests /session-close
        ↓
/session-close → state.md + chapters/index.md updated
        ↓
next session starts from updated state
```
