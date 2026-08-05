# /session-close

End-of-session protocol for Teller writing sessions.

## Steps

1. **Check for open continuity flags.** Ask the user: "¿Hay flags de continuidad sin resolver de esta sesión?" If yes, list them and stop — do not proceed until step 2 until all flags are resolved or explicitly dismissed.

2. **Propose state.md update.** Read `projects/[project]/state.md`. Propose updated values for:
   - `Last written` → this chapter
   - `Next` → next chapter (increment cap number)
   - `Where we are` → 2–3 sentence update based on what happened
   - `Next chapter plan` → clear or update to reflect new open threads
   Wait for user confirmation before writing.

3. **Load:** `projects/[project]/chapters/index.md`

4. **Propose a new row** for the chapter just written:
   ```
   | [cap#] | [title] | `[filename]` | [POV] | [key characters] | [one-line summary] |
   ```
   Wait for user confirmation before writing.

5. **Check `plot/structure.md` (if it exists for this project).** If the chapter just written closed an arc, opened a new one, or moved an arc boundary (e.g. inserted/removed a chapter mid-arc), propose an update to the relevant row(s) — Libro/Arco/Línea/Cap range/Estado. Wait for user confirmation before writing. Skip silently if the project has no `structure.md` or nothing structural changed this session.

6. **Offer update-nodes:** "¿Quieres que revise los nodos para actualizar canon del capítulo?" If yes, run update-nodes bundle. Propose diffs — do not apply without confirmation.

7. **Detect libro completion.** Check if the chapter just closed matches the final chapter of the last arc in `plot/structure.md` (fall back to `plot/arcs.md` if the project has no `structure.md`). If no final chapter is defined anywhere, ask: "¿Es este el último capítulo del libro?"

   If libro is complete:
   - Ask: "¿Marcamos Libro [N] como completo?"
   - If confirmed → add to `state.md`: `libro-[N]-status: complete` and `next-book-initialized: false`
   - Output:
     > "Libro [N] completo.
     > - `/new-book [N+1]` — siguiente libro en el mismo universo
     > - `/new-project [nombre]` — nueva obra, universo diferente"

   If libro is NOT complete → skip step 7 entirely. Do not mention it.

8. **Offer notes entry.** Ask: "¿Añadimos una nota de proceso al Cap [X]?" If yes → load `.claude/commands/notes.md` add-entry flow. If `projects/[project]/notes.md` does not exist, offer to create it first. Skip silently if user says no.

9. **Commit and push.** Run `git status` to show changed files. Propose a commit message in the format:
   ```
   session: cap [X] — [one-line summary of what was written]
   ```
   Ask: "¿Hacemos commit y push?" If confirmed → `git add -A && git commit -m "[message]" && git push origin master`.

## Notes

- Never apply changes without explicit user confirmation at each step.
- If user types `/session-close [cap number]` use that as the chapter to close.
- state.md update (step 2) is the most important — it's what orients the next session.
- Step 5 keeps `structure.md` from drifting the way `chapters/index.md` and `arcs.md` did before the 2026-08-05 cleanup — only trigger it on real structural change, not every chapter.
- Step 7 is conditional — only triggers when final chapter is detected or confirmed by user.
- Step 8 is optional — skip if user declines.
- Step 9 always runs last — even if previous steps were skipped.
