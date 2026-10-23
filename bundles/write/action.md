---
type: bundle
task: write/action
updated: 2026-10-23
---

# Bundle: Write / Action

## Load

- `projects/[project]/voice/style.md`
- `projects/[project]/themes/writing-rules.md`
- `projects/[project]/system/domains.md` — hard constraints on Domain use
- `projects/[project]/voice/combat.md` — universal combat rules (loads whenever there is a fight)
- `projects/[project]/voice/narration.md` — only if the scene uses onlookers, an elevated narrator or thought chains
- `projects/[project]/voice/combat-visual.md` — index only; then read just the one to three family files in `voice/combat-visual/` that fit the scene
- `projects/[project]/characters/[id].md` for each character present → follows their `load-with` to get `voice/pov-[id]` and `system/[domain]`

## Focus

Domain use must comply exactly with editorial rules in `system/`. Movement descriptions differ by character — load character node for their specific physical style.

## Constraints

- System rules are not suggestions — flag any scene that would require breaking them
- Park never runs to charge his Domain
- Domain descriptions per character must not converge — Park is intuitive, Pier is theoretical
- Physical cost and recovery must match established patterns
- Combat visual vocabulary: families are options, not templates; one or two per fight, never in the same order twice; take strategy only, never another work's concepts or names
