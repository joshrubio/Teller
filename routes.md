---
type: routes
updated: 2026-06-17
---

# Route Map

Path pattern: `projects/[project]/[module]/[node-id].md`

## System routes

| Route | Purpose |
|---|---|
| `manifest.md` | Entry point. Always load first. |
| `routes.md` | Full path map (this file). |
| `bundles/` | Task bundles |
| `_templates/` | Node templates for new entries |

## ledger-of-domains

| Route | Module | Content |
|---|---|---|
| `projects/ledger-of-domains/index.md` | — | Project entry point |
| `projects/ledger-of-domains/world/` | world | Lore, AMAT structure, locations, Odem |
| `projects/ledger-of-domains/characters/` | characters | Character nodes |
| `projects/ledger-of-domains/system/` | system | Domains, Odem mechanics, power rules |
| `projects/ledger-of-domains/plot/` | plot | Arcs, chapter beats, timeline |
| `projects/ledger-of-domains/relations/` | relations | Relationship web |
| `projects/ledger-of-domains/voice/` | voice | Style guide, narrative voice, reference works |
| `projects/ledger-of-domains/themes/` | themes | Thematic framework, motifs |
| `projects/ledger-of-domains/bestiary/` | bestiary | Potestades, anomaly classification |
| `projects/ledger-of-domains/chapters/` | chapters | Chapter navigation index |

## Bundles

| Route | Task | Trigger |
|---|---|---|
| `bundles/continuity-check.md` | Verify chapter against canon | User-invoked |
| `bundles/update-nodes.md` | Propose node updates after new chapter | User-invoked |
| `bundles/write/index.md` | Write — parent, infers sub-task | User-invoked or agent-inferred |
| `bundles/write/dialogue.md` | Write dialogue scenes | User-invoked or agent-inferred |
| `bundles/write/action.md` | Write action / Domain-use scenes | User-invoked or agent-inferred |
| `bundles/write/introspection.md` | Write introspective / internal scenes | User-invoked or agent-inferred |
| `bundles/session-close.md` | End-of-session protocol — update chapters index, offer update-nodes | Agent-prompted or user-invoked |
