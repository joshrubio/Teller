---
type: bundle
task: plan
updated: 2026-06-18
---

# Bundle: Plan

Detect granularity from input. Do not ask for clarification unless genuinely ambiguous.

## Level: Cap — "planifiquemos el cap X"

Load: `plot/arcs.md` + `state.md` + `relations/conflicts.md`

Output:
```
## Cap X — [working title]

**POV:** [character]
**Arc function:** [what this cap does narratively]
**Opening beat:** [first thing that happens]
**Beats:**
1. ...
2. ...
3. ...
**Closing beat / hook:**
**Open questions / canon needed:**
```

## Level: Batch — "los caps 38–42" / "los próximos N caps"

Load: `plot/arcs.md` + `state.md` + `relations/conflicts.md`

Output: flow table first, then beat sheets per cap on request or if N ≤ 3.

```
| Cap | POV | Arc function | Key beat |
|---|---|---|---|
```

## Level: Arc — "el arco X" / "¿cómo va el arco X?"

Load: `plot/arcs.md` + `plot/timeline.md`

Output: dramatic question for the arc, act structure (beginning / escalation / resolution), cap range, key beats per act, open threads entering and exiting.

## Level: Book — "el Libro X" / "¿cómo estructuramos el siguiente libro?"

Load: `state.md` + `plot/arcs.md` + open threads from previous book

Output: dramatic question proposal, 3-arc skeleton (1–2 sentences each), open threads feeding in. No beat sheets — structural only.

## Level: Event — user names a scene or moment without specifying a cap

Load: character nodes for people involved + `relations/conflicts.md` + `plot/arcs.md`

1. Determine where in the arc this event belongs
2. Output: which caps carry it + what each cap needs to contain

## Ambiguous input

"planifiquemos lo que sigue" → default to next-3 batch from `state.md → Next`. Show flow table, offer to go deeper.
