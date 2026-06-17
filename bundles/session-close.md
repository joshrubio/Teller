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

### Step 1 — Update chapters index

Read the chapter file at its path.
Extract:
- Chapter number
- POV character
- All named characters present
- Arc number
- One-line summary (what happens narratively, not thematically)

Propose entry for `projects/[project]/chapters/index.md`.
Wait for user confirmation before writing.

### Step 2 — Offer update-nodes

After Step 1 is confirmed, ask:
"Run update-nodes on this chapter?"

If yes → load `bundles/update-nodes.md` with the same chapter path.
If no → close session.

## Rule

Never auto-apply either step. Each step requires explicit user confirmation.
Step 2 is optional — not every chapter establishes new canon.
