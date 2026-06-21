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

5. **Offer update-nodes:** "¿Quieres que revise los nodos para actualizar canon del capítulo?" If yes, run update-nodes bundle. Propose diffs — do not apply without confirmation.

6. **Detect libro completion.** Check if the chapter just closed matches the final chapter of the last arc in `plot/arcs.md`. If `plot/arcs.md` has no defined final chapter, ask: "¿Es este el último capítulo del libro?"

   If libro is complete:
   - Ask: "¿Marcamos Libro [N] como completo?"
   - If confirmed → add to `state.md`: `libro-[N]-status: complete` and `next-book-initialized: false`
   - Output:
     > "Libro [N] completo.
     > - `/new-book [N+1]` — siguiente libro en el mismo universo
     > - `/new-project [nombre]` — nueva obra, universo diferente"

   If libro is NOT complete → skip step 6 entirely. Do not mention it.

7. **Offer notes entry.** Ask: "¿Añadimos una nota de proceso al Cap [X]?" If yes → load `.claude/commands/notes.md` add-entry flow. If `projects/[project]/notes.md` does not exist, offer to create it first. Skip silently if user says no.

8. **Commit and push.** Run `git status` to show changed files. Propose a commit message in the format:
   ```
   session: cap [X] — [one-line summary of what was written]
   ```
   Ask: "¿Hacemos commit y push?" If confirmed → `git add -A && git commit -m "[message]" && git push origin master`.

## Notes

- Never apply changes without explicit user confirmation at each step.
- If user types `/session-close [cap number]` use that as the chapter to close.
- state.md update (step 2) is the most important — it's what orients the next session.
- Step 6 is conditional — only triggers when final chapter is detected or confirmed by user.
- Step 7 is optional — skip if user declines.
- Step 8 always runs last — even if previous steps were skipped.
