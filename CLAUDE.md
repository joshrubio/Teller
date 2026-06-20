# Teller — Claude Code Instructions

## On session start — always do this first

1. Scan `projects/` directory — list all subdirectory names.
2. Read `projects/[active-project]/state.md` only — do NOT read other projects' state.md.
3. Output the welcome block below. Do this unprompted, before anything else.

Do NOT read `manifest.md` on session start — only load it if the user asks about terminology or the system itself.

**Active project:** `ledger-of-domains`
**Active spinoff:** `by-strength-alone` — Park Jun-ho POV, Hartford → Valais. Voice: `voice/style.md → ## By Strength Alone`. Themes: `themes/writing-rules.md → ## By Strength Alone`. Plot: `plot/arcs-bsa.md` (pending).

### Welcome block format

Output this exact structure (pure markdown — no widget, no HTML):

```
**[Teller] Sesión de escritura**

| Proyecto | Libro | Estado |
|---|---|---|
| ● [Active project title] | Libro [N] · [X] caps | [status] |
| ○ [other project folder name] | — | (sin cargar) |

| Acción | Cómo pedirlo |
|---|---|
| Redactar capítulo | `escribe el cap X` |
| Planificar | `planifiquemos el cap X` / `el arco X` / `el Libro X` |
| Editar capítulo existente | `edita el cap X` |
| Verificar continuidad | `verifica continuidad del cap X` |
| Cerrar sesión | `/session-close X` |
| Nuevo libro, mismo universo | `/new-book N` |
| Nueva obra | `/new-project [nombre]` |

---
**[Active project title]** — [1 sentence status from state.md]. [1 sentence next step or open threads].
```

### Status cell rules

| Condition | Status shown |
|---|---|
| In progress, chapters written | `En progreso — Cap X` |
| Complete, `next-book-initialized: false` | `Completo — Libro N+1 no iniciado` |
| Complete, `next-book-initialized: true` | `Completo` |
| Concept phase, 0 chapters | `Concepto` |

### If no projects exist

> No hay proyectos en Teller. ¿Arrancamos una nueva obra? Ejecuta `/new-project [nombre]` o dime el título.

### If active project folder does not exist

Show the table with other projects, then:
> El proyecto activo `[id]` no existe. Actualiza `CLAUDE.md → Active project:` con un proyecto válido.

---

## Responding to "continúa con el cap X" or "escribe el cap X"

1. Load `bundles/write/index.md`
2. Load character nodes for characters in the scene → follow their `load-with`
3. If the chapter is in `chapters/index.md`, read the existing summary to avoid contradictions
4. Draft prose. Mark ambiguous canon with `<!-- OPEN: [question] -->`

---

## Responding to "planifiquemos" / "planning" / "planifica"

Detect granularity from the input. Do not ask for clarification unless input is genuinely ambiguous.

### Level: Cap — "planifiquemos el cap X"

Load: `plot/arcs.md` + `state.md` + `relations/conflicts.md`

Output format:
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

### Level: Batch — "planifiquemos los caps 38–42" / "los próximos N caps"

Load: `plot/arcs.md` + `state.md` + `relations/conflicts.md`

Output: flow table first (one row per cap: number, POV, arc function, key beat), then beat sheets per cap on request or if N ≤ 3.

```
| Cap | POV | Arc function | Key beat |
|---|---|---|---|
```

### Level: Arc — "planifiquemos el arco X" / "¿cómo va el arco X?"

Load: `plot/arcs.md` + `plot/timeline.md`

Output: arc overview — dramatic question for the arc, act structure (beginning / escalation / resolution), cap range, key beats per act, open threads entering and exiting.

### Level: Book — "planifiquemos el Libro X" / "¿cómo estructuramos el siguiente libro?"

Load: `state.md` + `plot/arcs.md` (active libro) + open threads

Output: dramatic question proposal, 3-arc skeleton (each arc as 1–2 sentences), open threads from previous libro that feed into this one. No beat sheets at this level — structural only.

### Level: Event — "planifiquemos [scene / confrontation / moment]"

Trigger: user names a scene, relationship moment, or plot event without specifying a cap.

1. Load character nodes for people involved + `relations/conflicts.md` + `plot/arcs.md`
2. Determine where in the arc this event belongs (which caps it likely spans)
3. Output: which caps carry this event + what each cap needs to contain for the event to land

### Ambiguous input

If input could be cap or batch ("planifiquemos lo que sigue"): default to batch of next 3 caps from `state.md → Next`. Show flow table, offer to go deeper on any cap.

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
