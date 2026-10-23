---
id: voice-index
type: module-index
module: voice
project: ledger-of-domains
updated: 2026-10-23
---

# Voice

Load first in any write task. Rules here are constraints, not suggestions.

## Node roster

| ID | Name | Content | Status |
|---|---|---|---|
| `style` | Style guide | Prose rules, AI-detection patterns, editorial rules, dialogue formatting | Migrated |
| `pov-park` | POV: Park | Gestures, speech patterns, Domain description rules | Migrated |
| `pov-oliver` | POV: Oliver | Gestures, speech patterns, Odem analogy registry | Migrated |
| `pov-voss` | POV: Voss | Gestures, speech patterns, measurement constraint | Migrated |
| `pov-pier` | POV: Pier | Gestures, speech patterns, Domain description rules | Migrated |
| `pov-asha` | POV: Asha | Gestures, speech patterns, canonical phrase warning | Migrated |
| `pov-riku` | POV: Riku | Gestures, hand variant registry, speech patterns | Migrated |

| `pov-sisi` | POV: Sisi | Per-character voice file | Present |
| `pov-tomas` | POV: Tomás | Per-character voice file | Present |
| `narration` | Narration layers | Inner voice, elevated narrator (Cap5, Cap162), onlookers; load when a scene uses them | Active |
| `combat` | Combat narration | Sanderson model: spatial anchoring, micro-objectives, cause-effect chains; rule 14 narration inside a fight. Applies to LoD + BSA | Active |
| `combat-visual` | Combat visual vocabulary | Index of strategy families in `combat-visual/` (one file per family); read the index, then one to three families | Active |
| `combat-visual-log` | Combat visual source log | Record of references and inferences; never loaded when writing | Reference |

> Per-character POV files are loaded via `load-with` in each character node — not loaded globally.
> References (Naruto/HxH/JJK) moved to `_planning/references.md` — planning only.
