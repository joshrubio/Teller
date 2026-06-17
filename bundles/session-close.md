---
type: bundle
task: session-close
updated: 2026-06-17
---

# Bundle: Session Close

End-of-session protocol. Triggered by agent prompt or user invocation after a chapter is finished.

## When to trigger

Agent asks at session end: "Chapter [X] finished? Run session-close?"
User can also invoke directly.

## Steps

### Step 0 — Update state.md

Read `projects/[project]/state.md`.
Propose updated values:
- `Last written` → this chapter
- `Next` → next cap (increment)
- `Where we are` → 2–3 sentence narrative summary of current position
- `Next chapter plan` → clear existing plan or update with new open threads

Propose the full updated state.md. Wait for user confirmation before writing.
**This step is not optional** — state.md is what orients every future session.

### Step 1 — Check continuity flags

Ask: "¿Hay flags de continuidad sin resolver?"
If yes → stop here. Do not proceed until resolved or explicitly dismissed.

### Step 2 — Update chapters index

Read the chapter file.
Extract: chapter number, POV, named characters, arc, one-line summary.
Propose row for `projects/[project]/chapters/index.md`.
Wait for user confirmation before writing.

### Step 3 — Offer update-nodes

Ask: "¿Reviso los nodos para actualizar canon?"
If yes → load `bundles/update-nodes.md` with the chapter path. Propose diffs per node.
If no → close session.

## Rule

Never auto-apply any step. Each requires explicit user confirmation.
Step 3 is optional — not every chapter establishes new canon.
Step 0 is mandatory — never skip it.
