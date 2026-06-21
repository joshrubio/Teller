# /notes

Writing process journal. One file per project, organized by chapter.

## On invoke

### 1 — Detect project

Read active project from `state.md` (or ask if multiple projects active).

### 2 — Check if notes.md exists

Path: `projects/[project]/notes.md`

---

#### If file does NOT exist — scaffold

Ask three questions (one at a time):

1. "¿Cómo llamamos a este diario? (título libre — ej. *Notas de proceso — Ledger of Domains*)"
2. "Una línea: ¿de qué trata esta obra?"
3. "Escribe una intro personal — ¿por qué escribes esto? ¿qué esperas de este proceso?"

Then create `projects/[project]/notes.md`:

```markdown
---
id: notes
type: notes
project: [project-id]
updated: [YYYY-MM-DD]
---

# [Título]

> [Intro personal — verbatim from user, no edits]

---
```

Confirm: "Notas creadas. ¿Añadimos una primera entrada?"
If yes → go to **Add entry** below.

---

#### If file EXISTS — show menu

Read the file. Show:

```
## Notas — [Título]

Últimas entradas: Cap X, Cap Y, Cap Z

¿Qué hacemos?
  a) Añadir nota al cap [next cap inferred from state.md]
  b) Editar entrada existente
  c) Ver todas las entradas
```

---

## Add entry

Ask:
1. "¿Capítulo? (número o título)" — infer from context if session just closed
2. "¿Qué quieres anotar?" — free text, no length limit

Append to `projects/[project]/notes.md`:

```markdown
## Cap [X] — [Título si lo hay]

[Anotación verbatim — no paraphrase, no summarize]

---
```

Write immediately. Confirm: "Nota añadida al Cap [X]."

---

## Edit entry

Show numbered list of all existing `## Cap` entries.
User picks one (by number or cap number).

Show current content of that entry.
Ask: "¿Qué cambiamos?" — accept free text or instruction.

Apply edit. Show diff before writing. Wait for confirmation.

---

## Rules

- Never paraphrase or summarize user's words — copy verbatim.
- Never suggest what to write — only prompt and receive.
- `updated:` frontmatter field → refresh on every write.
- Do not create entries for caps that haven't been written yet.
