---
type: bundle
task: continuity-check
updated: 2026-06-17
---

# Bundle: Continuity Check

Verify that a chapter or scene does not contradict established canon.

## How to invoke

Provide: the chapter or scene text (or file path).
Output: flagged contradictions — exact quote from chapter + the node it contradicts. Report only. No rewrites.

## Nodes to load

Always:
- `projects/[project]/plot/arcs.md`
- `projects/[project]/relations/conflicts.md`
- `projects/[project]/system/domains.md`

Per scene (infer from characters present):
- `projects/[project]/characters/[character-id].md` for each character with a named presence

If scene involves Domain use:
- `projects/[project]/system/domains.md`

## What to check

- Character appearance details vs. node `Appearance` field
- Domain/power use vs. editorial rules in `system/` (hard constraints)
- Rank and mission history vs. character node mission table
- Relationship dynamics and subtext vs. `relations/`
- Canonical phrases and images — must not be contradicted
- Timeline consistency vs. `plot/arcs`
