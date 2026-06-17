# Teller — Claude Code Instructions

## On session start — always do this first

1. Read `manifest.md` — system entry point, defines all terminology.
2. Read `projects/[active-project]/state.md` — tells you exactly where the story is.
3. Give the user a one-paragraph orientation: current position + next chapter status. Do this unprompted.

**Active project:** `ledger-of-domains`

So on every session start, read:
- `manifest.md`
- `projects/ledger-of-domains/state.md`

Then say something like:
> "Ledger of Domains — [status from state.md]. Próximo: [next from state.md]. [2 sentences on open threads or next chapter plan]. ¿Continuamos con el planning o arrancamos a escribir?"

---

## Responding to "continúa con el cap X" or "escribe el cap X"

1. Load `bundles/write/index.md`
2. Load character nodes for characters in the scene → follow their `load-with`
3. If the chapter is in `chapters/index.md`, read the existing summary to avoid contradictions
4. Draft prose. Mark ambiguous canon with `<!-- OPEN: [question] -->`

---

## Responding to "continúa con el planning del cap X" or "planifiquemos el cap X"

1. Load `plot/arcs.md`
2. Load `projects/ledger-of-domains/state.md`
3. Load `relations/conflicts.md` (open threads)
4. Produce: a beat sheet for cap X. Format:

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

---

## End of session

Run `/session-close` — updates state.md, chapters/index.md, and proposes node diffs.

---

## System language

- All node files: English
- Prose content (chapters, dialogue): any language
- This file: English
