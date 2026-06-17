# /session-close

End-of-session protocol for Teller writing sessions.

## Steps

1. **Check for open continuity flags.** Ask the user: "¿Hay flags de continuidad sin resolver de esta sesión?" If yes, list them and stop — do not proceed until resolved or explicitly dismissed.

2. **Load:** `projects/[project]/chapters/index.md`

3. **Propose a new row** for the chapter just written. Use this format:
   ```
   | [cap#] | [title] | `[filename]` | [POV] | [key characters] | [one-line summary] |
   ```
   Wait for user to confirm before writing to the file.

4. **Offer update-nodes:** "¿Quieres que revise los nodos para actualizar canon del capítulo?" If yes, run the update-nodes bundle on the chapter. Propose diffs per node — do not apply without confirmation.

## Notes

- Never apply changes to nodes or chapters/index.md without explicit user confirmation at each step.
- If the user types `/session-close [cap number]` pass that as context for which chapter to close.
