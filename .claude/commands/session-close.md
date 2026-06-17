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

## Notes

- Never apply changes without explicit user confirmation at each step.
- If user types `/session-close [cap number]` use that as the chapter to close.
- state.md update (step 2) is the most important — it's what orients the next session.
