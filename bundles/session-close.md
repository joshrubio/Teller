---
type: bundle
task: session-close
updated: 2026-06-17
---

# Bundle: Session Close

End-of-session protocol. Triggered by agent prompt or user invocation after a chapter is finished.

## When to trigger

Agent asks at session end: "Chapter [X] finished? Run session-close?"
User can also invoke directly.

## Steps

### Step 0 — Update state.md

Read `projects/[project]/state.md`.
Propose updated values:
- `Last written` → this chapter
- `Next` → next cap (increment)
- `Where we are` → 2–3 sentence narrative summary of current position
- `Next chapter plan` → clear existing plan or update with new open threads

Propose the full updated state.md. Wait for user confirmation before writing.
**This step is not optional** — state.md is what orients every future session.

### Step 1 — Check continuity flags

Ask: "¿Hay flags de continuidad sin resolver?"
If yes → stop here. Do not proceed until resolved or explicitly dismissed.

### Step 2 — Update chapters index

Read the chapter file.
Extract: chapter number, POV, named characters, arc, one-line summary.
Propose row for `projects/[project]/chapters/index.md`.
Wait for user confirmation before writing.

### Step 3 — Offer update-nodes

Ask: "¿Reviso los nodos para actualizar canon?"
If yes → load `bundles/update-nodes.md` with the chapter path. Propose diffs per node.
If no → continue to Step 4.

### Step 4 — Detect libro completion

Check: does the chapter just closed match the final chapter of the last arc in `plot/arcs.md`?
If `plot/arcs.md` has no defined final chapter → ask: "¿Es este el último capítulo del libro?"

If libro is complete:
1. Ask: "¿Marcamos Libro [N] como completo?"
2. If confirmed → add to `state.md`:
   ```
   libro-[N]-status: complete
   next-book-initialized: false
   ```
3. Output:
   > "Libro [N] completo.
   > - `/new-book [N+1]` — siguiente libro en el mismo universo
   > - `/new-project [nombre]` — nueva obra, universo diferente"

If libro is NOT complete → skip this step entirely. Do not mention it.

### Step 5 — Commit and push

Run `git status`. Show changed files.
Propose commit message:
```
session: cap [X] — [one-line summary of what was written]
```
Ask: "¿Hacemos commit y push?"
If confirmed → `git add -A && git commit -m "[message]" && git push origin master`.

## Rule

Never auto-apply any step. Each requires explicit user confirmation.
Step 3 is optional — not every chapter establishes new canon.
Step 4 is conditional — only runs if final chapter detected or confirmed.
Step 5 always runs last — even if previous steps were skipped.
Step 0 is mandatory — never skip it.
