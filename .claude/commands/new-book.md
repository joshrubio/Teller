# /new-book [N]

Transitions the active project to a new libro within the same universe. Does NOT create a new project folder — world, system, and character nodes are shared. Only libro-specific layers (voice, themes, plot) are versioned.

## When to use

- Continuing the same universe in a new libro (sequel, next arc, same cast)
- Triggered automatically by session-close when Libro N is marked complete
- User can also run directly: `/new-book 2`

## NOT for

- Unrelated new story in a different universe → use `/new-project [nombre]`

---

## Steps

### 1. Confirm scope

Ask:
> "¿Qué cambia en el Libro [N] respecto al anterior? Marca lo que aplica:
> - Voz / registro de la prosa
> - Ritmo (ej: cliffhangers, pacing)
> - Temas nuevos
> - Combinación de los anteriores"

Wait for answer before continuing.

### 2. Voice — add section to voice/style.md

Read `projects/[project]/voice/style.md`.

If the file has no `## Libro X` sections yet:
- Wrap existing content under `## Libro 1`

Add new section:
```markdown
## Libro [N]

[Ask user: what changes in register/tone? What stays the same from Libro N-1?]

### Changes from Libro [N-1]
- [user-provided changes]

### Cliffhanger / rhythm rule (if applicable)
- [user-provided rhythm changes]

### What stays the same
- [inherited from previous libro — agent fills from existing content]
```

Propose the full updated file. Wait for confirmation. Write.

### 3. Themes — add section to themes/writing-rules.md (or themes/libro[N].md if themes/ is split)

Read existing themes file.

Add:
```markdown
## Libro [N]

### New themes
- [user-provided]

### Threads continued from Libro [N-1]
- [agent extracts from plot/arcs.md open threads — user confirms]
```

Propose. Wait for confirmation. Write.

### 4. Create plot/arcs-libro[N].md

Ask:
> "Para el Libro [N] necesito:
> 1. Pregunta dramática
> 2. Incidente incitante
> 3. Objetivo del Arco 1
>
> Arcos 2 y 3 pueden ser TBD."

Create `projects/[project]/plot/arcs-libro[N].md` with user answers. Propose. Wait. Write.

### 5. Update state.md

Add / update:
```yaml
active-libro: [N]
next-book-initialized: true
libro-[N-1]-status: complete
```

Update `Status` section:
```
- Libro [N-1]: complete ([X] caps)
- Libro [N]: concept phase — 0 chapters written
```

Propose. Wait for confirmation. Write.

### 6. Update CLAUDE.md

Edit:
- `Active libro: [N]`
- Load voice line: `projects/[project]/voice/style.md → ## Libro [N] section`

Propose change. Wait for confirmation. Write.

---

## After all steps confirmed

Output:
> "Libro [N] inicializado. Voice y temas versionados. Cuando quieras: `planifiquemos el cap [first cap of libro N]`."

---

## Rules

- Never delete or overwrite Libro N-1 voice/themes sections — they stay as reference
- Do not suggest plot ideas or character arcs the user has not provided
- Each step requires explicit confirmation before writing
