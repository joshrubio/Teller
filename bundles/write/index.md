---
type: bundle
task: write
updated: 2026-06-21
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

## Default context (always, no exceptions)

- `projects/[project]/state.md` — active chapter, next step, open threads
- `projects/[project]/voice/style.md` — narrative voice, rhythm, POV rules

Nothing else loads automatically.

## Demand-driven loading

Load a node only when one of these is true:

1. **User declares it upfront** — "escribe cap X, necesito a Oliver y Voss" → load those nodes immediately.
2. **Scene requires it** — agent hits a moment needing a specific node (character voice, Domain rule, location detail). Agent pauses and asks: "Necesito el nodo de [X] para esta escena. ¿Lo cargo?" User says yes/no/provides inline.
3. **User asks mid-write** — "¿cómo reacciona Kaspar aquí?" → load `characters/kaspar.md` before answering.

Never load `voice/style.md`, `themes/`, or character nodes speculatively. Load only when the scene demands it.

## Inline provision (skip the load)

User can provide context inline instead of loading a node:
> "Voss habla frío, clínico, nunca levanta la voz"

Agent uses that. No node load needed.

## After delivering a complete chapter

End your response with:
> "Cap [X] completo. Ejecuta `/session-close [X]` para cerrar la sesión."

Trigger: prose ends at a clear narrative stopping point (chapter end), not mid-scene.
