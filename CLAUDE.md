# Teller — Claude Code Instructions

## On session start — always do this first

1. Read `manifest.md` — system entry point, defines all terminology.
2. Read `projects/[active-project]/state.md` — tells you exactly where the story is.
3. Output the welcome block below. Do this unprompted, before anything else.

**Active project:** `ledger-of-domains`

So on every session start, read:
- `manifest.md`
- `projects/ledger-of-domains/state.md`

### Welcome block format

Output exactly this structure (fill brackets from state.md):

---

**Teller** — story bible en `D:\Writting\Teller\`

Comandos disponibles:
| Comando | Para qué |
|---|---|
| `escribe el cap X` | Redactar un capítulo |
| `planifiquemos el cap X` | Planificar un capítulo |
| `verifica continuidad del cap X` | Revisar continuidad |
| `/session-close X` | Cerrar sesión tras un capítulo |
| `/new-project [nombre]` | Iniciar una nueva obra |

---

**Proyecto activo:** [title from state.md]
[1 sentence: current status — e.g. "Libro 1 completo (37 caps). En fase de planning para Libro 2."]
[1 sentence: next step — e.g. "Próximo: planning del Cap 38."]

¿Continuamos con [active project] o iniciamos una nueva obra?

---

If `Active project: none` or the project folder does not exist, replace the bottom block with:
> No hay proyecto activo. ¿Arrancamos una nueva obra? Ejecuta `/new-project [nombre]` o dime el título.

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
