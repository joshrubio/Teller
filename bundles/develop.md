---
type: bundle
task: develop
updated: 2026-06-17
---

# Bundle: Develop — New Project Intake

For new projects with no existing nodes. Guides user through providing the exact data each node template requires. Does NOT brainstorm — asks for specific fields, builds nodes from answers.

## Trigger

- User runs `/new-project [name]`
- User says: "quiero empezar un libro", "nueva historia", "new story", "tengo una idea para una historia", "empecemos un proyecto nuevo", "quiero escribir una historia"
- `CLAUDE.md → Active project:` points to a folder that does not exist

## Two modes

| Mode | Trigger | Behavior |
|---|---|---|
| **Structured** | User says "quiero empezar", no prior story content given | Ask field by field in order, Steps 1–6 |
| **Parse** | User arrives with narrative description, partial ideas, or story fragments | Extract first → show map → ask only for missing fields |

### Parse mode — extract-first rule

When the user provides any narrative input (character description, plot idea, scene concept), do NOT ignore it and start the intake from scratch.

Instead:
1. Parse the input → identify which node types are touched (character / world / plot / voice)
2. Extract every explicit data point and map it to a node field
3. Show the user what was extracted:

```
Identifiqué esto:

**[Node type]:**
- [field]: [extracted value]
- [field]: [extracted value]
- TBD: [missing fields]

**[Node type]:**
- ...

¿Completamos los campos faltantes?
```

4. Ask only for TBD fields — never re-ask for data already provided
5. If input touches multiple node types simultaneously → show all extractions at once, then resolve TBDs node by node

### Core rule (both modes)

Do NOT suggest plot ideas, character traits, themes, or names the user has not provided.  
Ask for fields. If user doesn't know a field → write `<!-- TBD -->` and move on.  
One node at a time. Propose the file content. Wait for user confirmation. Write. Then next node.

---

## Intake order

| Step | Node created | Source |
|---|---|---|
| 1 | `index.md` | User answers |
| 2 | `state.md` | Auto-generated — no questions |
| 3 | `characters/[protagonist].md` | User answers — maps to `_templates/character.md` |
| 4 | `world/[setting].md` | User answers — maps to `_templates/world-node.md` |
| 5 | `voice/style.md` | User answers |
| 6 | `plot/arcs.md` | User answers |

---

## Step 1 — index.md

Ask:

> **Proyecto.** Necesito estos datos:
> 1. Título (o título de trabajo)
> 2. Logline: quién es el protagonista, qué quiere, qué se lo impide (1–2 frases)
> 3. Género o etiquetas (ej: fantasía, thriller, sci-fi, contemporáneo)
>
> Si no sabes un campo, di "TBD".

Node fields populated:
- `id` ← slugified title
- `# Title`
- `logline`
- `tags`

---

## Step 2 — state.md

Auto-generate without questions:

```yaml
---
id: state
type: project-state
project: [project-id]
updated: [today]
---
```

```
## Status
- Libro 1: concept phase — 0 chapters written

## Last written
None.

## Next
Cap 1 — not yet planned.

## Where we are
Project initialized. No chapters written. Bible in progress.

## Open threads
<!-- TBD — add as story develops -->

## Planning checklist for Cap 1
- [ ] Finish bible intake (Steps 3–6)
- [ ] Plan Cap 1 with `planifiquemos el cap 1`
```

---

## Step 3 — characters/[protagonist].md

Ask:

> **Protagonista.** Necesito estos datos:
> 1. Nombre
> 2. Rol en la historia (1 frase — ej: "detective que investiga su propio crimen")
> 3. Edad aproximada
> 4. ¿Qué quiere al inicio de la historia?
> 5. ¿Qué se lo impide (obstáculo externo o interno)?
> 6. ¿Cómo habla? (registro: frío/cálido/formal/fragmentado/sarcástico + 1 frase de ejemplo si tienes)
>
> Si no sabes un campo, di "TBD".

Node fields populated (from `_templates/character.md`):
- `id`, `# Name — Role`
- `Profile.Age`
- `Mission / arc history` ← what they want + what stops them
- `Voice patterns` ← how they talk

Leave blank: `Appearance`, `Domain`, `Rank`, `POV chapters`, `Personality`, `Canonical gestures`, `Family / background`, `Key relations`.

---

## Step 4 — world/[setting].md

Ask:

> **Mundo / escenario.** Necesito estos datos:
> 1. ¿Dónde transcurre la historia? (lugar físico + época)
> 2. ¿Qué 2–3 reglas diferencian este mundo del nuestro? (pueden ser físicas, sociales, o de poder)
> 3. ¿Qué institución o estructura de poder interactúa con el protagonista?
>
> Si no sabes un campo, di "TBD".

Node fields populated (from `_templates/world-node.md`):
- `# Title` ← place/setting name
- `Summary` ← place + time period
- `Rules / constraints` ← 2-3 world rules
- `Connected nodes` ← institution

---

## Step 5 — voice/style.md

Ask:

> **Voz.** Necesito estos datos:
> 1. Registro general de la prosa (ej: frío y contenido / cálido y expansivo / fragmentado / lírico)
> 2. Tres textos de referencia cuya prosa se parezca a lo que buscas (libros, autores, o fragmentos)
> 3. Tipo de POV (primera persona / tercera limitada / tercera omnisciente)
>
> Si no sabes un campo, di "TBD".

---

## Step 6 — plot/arcs.md

Ask:

> **Estructura.** Necesito estos datos:
> 1. Pregunta dramática del libro (ej: "¿puede Oliver preservar su humanidad mientras el Registro lo transforma?")
> 2. Incidente incitante: ¿qué obliga al protagonista a moverse al inicio?
> 3. Objetivo del Arco 1: ¿qué persigue el protagonista en la primera parte?
>
> Arcos 2 y 3 pueden ser TBD — se llenan después.

---

## After all 6 steps confirmed

1. Scaffold all module folders for the project (see `/new-project` command for list)
2. Update `CLAUDE.md` → change `Active project:` to new project id
3. Say:
   > "Proyecto [title] inicializado. Bible mínima lista. Cuando quieras: `planifiquemos el cap 1`."

---

## What NOT to do

- Do not suggest character names, traits, plot ideas, or themes
- Do not generate content the user has not provided
- Do not skip confirmation between nodes
- Do not move to Step N+1 until Step N file is confirmed and written
