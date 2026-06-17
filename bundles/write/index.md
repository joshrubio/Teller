---
type: bundle
task: write
updated: 2026-06-17
---

# Bundle: Write

Parent task. Infers sub-task from scene description, or user calls a sub-task directly.

## Sub-tasks

| Sub-task | Route | When to use |
|---|---|---|
| Dialogue | `bundles/write/dialogue.md` | Scene is primarily characters talking |
| Action | `bundles/write/action.md` | Scene involves combat, Domain use, physical conflict |
| Introspection | `bundles/write/introspection.md` | Scene is internal — POV character processing events alone |

## Inference rules

- Primary content is dialogue → `dialogue`
- Domain activation, combat, physical stakes present → `action`
- Solo POV, no dialogue, no combat → `introspection`
- Scene mixes types → load multiple sub-task bundles

## Always load first (before sub-task)

- `projects/[project]/voice/style.md`
- `projects/[project]/themes/writing-rules.md`

Then load character-specific POV: each character node declares `load-with: [voice/pov-[id]]` — follow those links.
Do NOT load `voice/index.md` or `themes/index.md` globally — too broad.

## After delivering a complete chapter

End your response with:
> "Cap [X] completo. Ejecuta `/session-close [X]` para cerrar la sesión."

Trigger: prose ends at a clear narrative stopping point (chapter end), not mid-scene.
