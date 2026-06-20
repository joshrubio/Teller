---
type: bundle
task: edit
updated: 2026-06-18
---

# Bundle: Edit

For editing or revising any chapter regardless of book completion status.

## If triggered without a specific chapter

Ask:
> "¿Qué quieres trabajar?
> - Planificar un capítulo específico
> - Editar o revisar un capítulo ya escrito
> - Revisar continuidad de un capítulo"

## If editing a specific chapter

1. Read `projects/[project]/chapters/index.md` → find which book cap X belongs to
2. Load `voice/style.md → ## Book [N]` section for that book
3. Load `themes/` section for that book
4. Load character nodes present in the scene
5. Read the manuscript file (path from chapters/index.md)
6. Edit. Mark ambiguous canon with `<!-- OPEN: [question] -->`

## After editing

- Propose updated row in `chapters/index.md` if summary changed
- Do NOT update `state.md` — past edits don't change active progression
- Do NOT suggest `/session-close`
