# /spinoff-idea [universe]

Generates a standalone story pitch set in an existing Teller universe — connected in world-rules only, independent in plot. Does not touch the active project's manuscript, state, or CLAUDE.md pointers. Output is a structure, not chapters, unless the user explicitly asks for chapters.

## When to use

User wants to explore a new book/spinoff idea inside an established universe without risking continuity of the main work, or wants a creative-capability check.

## Steps

1. **Pick universe.** If `[universe]` given, use it. Otherwise ask which project's world to draw from.
2. **Load world-only context** — the universe's `world/` nodes and `system/` (mechanics) nodes. Do NOT load `plot/`, `characters/` of the active story, or `chapters/`. The point is reusing physics, not reusing plot.
3. **Ask or infer constraints** before drafting — do not default silently:
   - Which in-world systems/institutions are off-limits for this pitch (e.g. "no AMAT")?
   - Should genre diverge from the source work, or stay adjacent?
   - Any element that must carry over (e.g. "must use Odem")?
4. **Divergence checklist** — before writing, verify the pitch does NOT:
   - Reuse the same protagonist archetype-to-plot mapping as an existing book (e.g. "protagonist perceives what others can't → institution recruits them → protagonist gets marked").
   - Reuse the same antagonist *shape* (entity that must be detected/fought) unless asked.
   - Default to a real-world setting chosen only because it's a trending headline association (e.g. picking a region solely because it's stereotypically linked to the story's device). Pick setting for a reason stated in the pitch.
   - Reuse institutional machinery (ranks, agencies, field-agent structure) unless the user asked to keep it.
5. **Draft the pitch**, in this order:
   - Logline
   - Genre (state explicitly, and how it differs from the source work)
   - Setting + why this setting (one sentence, must not be "because it's underused" alone)
   - Mechanic-specific rule: how the universe's core system manifests differently for this book's characters than in the existing work
   - Protagonist(s) — role, want, flaw
   - Central dramatic question
   - Indirect connection to the universe — one detail max, non-functional to plot (a name-drop, a rumor, nothing that requires the reader to know the source work)
   - Structure: parts/acts with beat bullets — NOT prose chapters, unless user explicitly asked for chapters
6. **Canon check** — if the pitch surfaces that a term or mechanic in a world node is scoped to a specific character's idiolect/technical framing rather than universal in-world terminology, flag it. Propose the exact edit. Do not edit the canon node without explicit confirmation — other stories may depend on that file.
7. **Save.** Write the pitch to `_ideas/[universe]/[slug].md` (create the folder if absent) with frontmatter: `type: idea`, `universe`, `uses: []`, `excludes: []`, `genre`, `status: pitch`, `updated`. Add a row to `_ideas/README.md`'s index table. Do NOT touch `projects/[universe]/state.md`, `CLAUDE.md`, or `manifest.md` — pitches are inert until promoted.

## Promotion

If the user wants to actually write this: `/new-project [name]` — it does not auto-graduate from `_ideas/`.

## Notes

- `_ideas/` is intentionally outside `projects/` so it's never picked up by the session-start scan in `CLAUDE.md`.
- Multiple pitches can exist per universe. Don't overwrite an existing pitch file without asking.
