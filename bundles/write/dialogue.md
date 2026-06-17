---
type: bundle
task: write/dialogue
updated: 2026-06-17
---

# Bundle: Write / Dialogue

## Load

- `projects/[project]/voice/style.md`
- `projects/[project]/themes/writing-rules.md`
- `projects/[project]/relations/[relevant-web].md` — subtext is in the relationship, not the words
- `projects/[project]/characters/[id].md` for each character with lines → follows their `load-with` to get `voice/pov-[id]`

## Focus

Voice patterns differ by character — load each character node and apply their documented voice pattern. Relations node informs what is not said. Silence is information.

## Constraints

- Apply dialogue formatting rules from `voice/dialogue-rules.md`
- Do not fill silences characters would not fill
- Character voice takes priority over exposition convenience
