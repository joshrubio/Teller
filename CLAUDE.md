# Teller — Claude Code Instructions

## On session start — always do this first

1. Read `manifest.md` — system entry point, defines all terminology.
2. Scan the `projects/` directory — list all subdirectory names.
3. For each project folder found, read its `state.md`.
4. Load `bundles/dashboard.md` — fill all data slots from state.md files.
5. Call show_widget with the filled HTML template. Do this unprompted, before anything else.

**Active project:** `ledger-of-domains`

### Welcome block format

Output exactly this structure:

---

**Teller** — `D:\Writting\Teller\`

**Proyectos**

| Proyecto | Libro activo | Estado |
|---|---|---|
| [title from each state.md] | Libro [N] | [status — see rules below] |

Comandos: `escribe el cap X` · `planifiquemos el cap X` · `verifica continuidad del cap X` · `/session-close X` · `/new-book N` · `/new-project [nombre]`

---

**Activo:** [active project title] — [1 sentence: current position from state.md]
[1 sentence: next step from state.md]

¿Continuamos con [active project] o cambiamos de proyecto?

---

### Status column rules

Derive from each project's `state.md`:

| Condition | Status shown |
|---|---|
| Libro N in progress, chapters written | `En progreso — Cap X` |
| Libro N complete, `next-book-initialized: false` | `Completo — Libro N+1 no iniciado` |
| Libro N complete, `next-book-initialized: true` | `Completo` |
| concept phase, 0 chapters | `Concepto — sin caps` |

### If no projects exist

Replace entire block with:
> No hay proyectos en Teller. ¿Arrancamos una nueva obra? Ejecuta `/new-project [nombre]` o dime el título.

### If active project folder does not exist

Output the projects table (other projects still listed), then:
> El proyecto activo `[id]` no existe. Actualiza `CLAUDE.md → Active project:` con un proyecto válido.

---

## Responding to "continúa con el cap X" or "escribe el cap X"

1. Load `bundles/write/index.md`
2. Load character nodes for characters in the scene → follow their `load-with`
3. If the chapter is in `chapters/index.md`, read the existing summary to avoid contradictions
4. Draft prose. Mark ambiguous canon with `<!-- OPEN: [question] -->`

---

## Responding to "continúa con el planning del cap X" or "planifiquemos el cap X"

1. Load `plot/arcs.md`
2. Load `projects/ledger-of-domains/state.md`
3. Load `relations/conflicts.md` (open threads)
4. Produce: a beat sheet for cap X. Format:

```
## Cap X — [working title]

**POV:** [character]
**Arc function:** [what this cap does narratively]
**Opening beat:** [first thing that happens]
**Beats:**
1. ...
2. ...
3. ...
**Closing beat / hook:**
**Open questions / canon needed:**
```

---

## Responding to "quiero editar" / "editar libro" / "volver a un capítulo"

Trigger phrases: "quiero editar", "editar libro", "volver al cap", "revisar algo", "edita el cap X", "revisa el cap X"

When triggered without a specific chapter, ask:
> "¿Qué quieres trabajar?
> - Planificar un capítulo específico
> - Editar o revisar un capítulo ya escrito
> - Revisar continuidad de un capítulo"

Then follow the path the user chooses. Works for ANY chapter in ANY libro regardless of completion status.

**If editing a specific chapter:**
1. Read `projects/[project]/chapters/index.md` → find which libro cap X belongs to
2. Load voice section for that libro: `voice/style.md → ## Libro [N]`
3. Load `themes/` section for that libro
4. Load character nodes present in the scene
5. Read the manuscript file (path from chapters/index.md)
6. Edit. Mark ambiguous canon with `<!-- OPEN: [question] -->`

**After editing:**
- Propose updated row in `chapters/index.md` if summary changed
- Do NOT update `state.md` — past edits don't change active progression
- Do NOT suggest `/session-close`

---

## After completing a chapter

When you deliver a complete chapter draft (full prose, not a partial scene), end your response with:

> "Cap [X] completo. Ejecuta `/session-close [X]` para cerrar la sesión."

Do this every time without waiting to be asked. A complete chapter = the prose ends at a clear narrative stopping point, not mid-scene.

---

## Responding to "quiero empezar un libro" / "nueva historia" / similar

Trigger phrases (any language, any variation):
- "quiero empezar un libro / historia / proyecto"
- "nueva historia / new story / new book"
- "tengo una idea para una historia / libro"
- "empecemos un proyecto nuevo"
- "quiero escribir una historia"

When detected:
1. Confirm: "¿Arrancamos un proyecto nuevo en Teller?"
2. If yes: ask for working title or name if not provided.
3. Load `bundles/develop.md` and run the intake protocol (Steps 1–6).
4. Do NOT trigger this if user is clearly talking about an existing project.

Alternatively: user can run `/new-project [name]` directly — same intake, skips confirmation.

---

## End of session

Run `/session-close` — updates state.md, chapters/index.md, and proposes node diffs.

---

## System language

- All node files: English
- Prose content (chapters, dialogue): any language
- This file: English
