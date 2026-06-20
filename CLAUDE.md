# Teller — Claude Code Instructions

**Active project:** `ledger-of-domains`

## On session start

1. Scan `projects/` — list subdirectory names.
2. Read `state.md` for EVERY project folder found.
3. Output welcome block (unprompted):

```
**[Teller] Sesión de escritura**

| Proyecto | Book | Estado |
|---|---|---|
| ● [title] | Book [N] · [X] caps | [status] |
| ○ [other folder] | — | (sin cargar) |

| Acción | Cómo pedirlo |
|---|---|
| Redactar | `escribe el cap X` |
| Planificar | `planifiquemos el cap X / el arco X / el Libro X` |
| Editar | `edita el cap X` |
| Continuidad | `verifica continuidad del cap X` |
| Cerrar sesión | `/session-close` |
| Nuevo libro | `/new-book N` |
| Nueva obra | `/new-project [nombre]` |

---
[title] — [1 sentence status]. [1 sentence next step / open threads].
```

Status rules: in-progress → `En progreso — Cap X` · complete + next-book-initialized:false → `Completo — Book N+1 no iniciado` · complete → `Completo` · concept → `Concepto`

Do NOT read `manifest.md` on session start.

## Routing

| User input | Load |
|---|---|
| `escribe` / `continúa con el cap` | `bundles/write/index.md` → character nodes via load-with |
| `planifiquemos` / `planifica` / `planning` | `bundles/plan.md` |
| `edita` / `revisa` / `quiero editar` | `bundles/edit.md` |
| `verifica continuidad` | `bundles/continuity-check.md` |
| `quiero empezar` / `nueva historia` / `new story` | confirm → `bundles/develop.md` |
| `/session-close` | `.claude/commands/session-close.md` |
| `/new-book` | `.claude/commands/new-book.md` |
| `/new-project` | `.claude/commands/new-project.md` |

After delivering a complete chapter, end with:
> "Cap [X] completo. Ejecuta `/session-close` para cerrar la sesión."

## System language

- Node files: English
- Prose content: any language
