---
version: 0.1.0-draft
type: agents-spec
updated: 2026-06-17
---

# AGENTS.md — Teller Agent Specification

> **Status: Draft.** This file defines how autonomous agents should interact with the Teller system. Implement against this spec when building automation on top of Teller.

---

## What an agent is

An agent is any AI process (Claude Code, API call, sub-agent) that uses Teller nodes to perform a bounded writing task. Agents do not write to nodes autonomously — they propose changes and wait for user confirmation.

**Rule:** an agent reads freely, proposes changes in structured diffs, and never applies them without explicit user approval.

---

## Available agents

### `continuity-agent`

**Purpose:** verify a chapter or scene does not contradict established canon.

**Entry:** `bundles/continuity-check.md`

**Input:** chapter file path or raw text.

**Output:** list of flagged contradictions only. Format:

```
## Flags

- [QUOTE from chapter] ↔ contradicts [node path:field]
  Reason: [one line]
```

No rewrites. No suggestions beyond the flag.

**When to invoke:** after finishing a chapter draft, before session-close.

---

### `update-nodes-agent`

**Purpose:** propose node diffs after new canon is established in a chapter.

**Entry:** `bundles/update-nodes.md`

**Input:** chapter file path or raw text + list of character nodes to check.

**Output:** structured diff proposals per node. Format:

```
## Proposed diffs

### characters/oliver.md
- field: Registry tracker
  current: "Ancla (Sabine, Cap 24 accidental)"
  proposed: "Ancla — integración estable. Usada en combate real Cap 35."
  reason: Cap 35 establishes first combat use.
```

User approves or rejects each diff individually. Agent does not apply.

**When to invoke:** after continuity-agent passes (no flags, or flags resolved).

---

### `write-agent`

**Purpose:** draft prose for a scene.

**Entry:** `bundles/write/index.md` — always load first; infers sub-task (dialogue / action / introspection).

**Input:** scene brief: characters present, location, what needs to happen narratively.

**Output:** draft prose in Markdown (`.md`). Marks any decision points where canon is ambiguous with `<!-- OPEN: [question] -->`.

**Publishing pipeline:** Markdown source → HTML for platform upload.
- RoyalRoad: paste HTML into chapter editor (source mode). Convert with Pandoc: `pandoc chapter.md -o chapter.html`
- Wattpad: paste Markdown text directly — basic formatting (bold, italic, line breaks) renders natively.
- No platform-specific formatting in the source `.md` — keep it clean; apply conversion at publish time.

**Constraints:**
- Must apply voice patterns from `voice/pov-[id]` for the POV character.
- Must not break editorial rules in `system/`.
- Must not invent new canon — if a scene requires new canon, flag it explicitly.

---

### `session-close-agent`

**Purpose:** end-of-session cleanup.

**Entry:** `.claude/commands/session-close.md`

**Steps:** see entry file — 7 steps (continuity flags → state.md → chapters index → update-nodes → libro completion → commit + push).

**When to invoke:** at end of any writing session where a chapter was finished or significantly revised.

**Invoke as:** Claude Code slash command `/session-close` (see `.claude/commands/session-close.md`).

---

## Multi-agent coordination

When running multiple agents in sequence on the same chapter:

```
continuity-agent → (resolve flags) → update-nodes-agent → (apply approved diffs) → session-close-agent
```

Agents share no memory between invocations. Each is cold-started with its bundle. Pass the chapter path explicitly to each.

**No parallel writes.** If two agents are active, the second waits until the first has completed its propose-confirm cycle.

---

## Context loading protocol

Every agent must load nodes in this order:

1. `manifest.md` — system entry point
2. Bundle file(s) for the task
3. Nodes declared in bundle `load-with`
4. Character nodes for characters in scope → follow their `load-with` recursively (max 1 level)

Do not load nodes not listed in step 2–4. Excess context = noise.

---

## What agents must never do

- Apply a diff to a node without user confirmation.
- Invent domain mechanics not in `system/`.
- Write new canonical dialogue in `update-nodes` output (diffs only).
- Load `_planning/` nodes during write tasks.
- Skip the `load-with` chain for characters.
