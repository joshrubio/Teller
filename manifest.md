---
version: 0.1.0
type: manifest
updated: 2026-06-17
---

# Teller

Structured story bible framework for AI-assisted fiction writing.

## How to use

1. Load this file first.
2. Load `routes.md` for the full path map.
3. Navigate to your project: `projects/[project-name]/index.md`
4. For a specific task, load the relevant bundle from `bundles/`.

## Core concepts

| Term | Analogy | Definition |
|---|---|---|
| **Node** | React component | A `.md` file with structured frontmatter. Atomic unit of canon. |
| **Module** | Next.js route segment | A category of nodes (`/characters`, `/world`, etc.) |
| **Bundle** | Context window preset | A predefined set of nodes for a specific AI task |
| **Route** | File-based route | Path pattern: `projects/[project]/[module]/[node-id]` |
| `load-with` | Import statement | Frontmatter field — nodes that must load alongside this one |

## Projects

| Project | Path | Status |
|---|---|---|
| Ledger of Domains | `projects/ledger-of-domains/` | Active |

## Notes

- System language: English. Node content may be in any language.
- `load-with` is the key to precision — nodes declare their own dependencies.
- Bundles are not exhaustive; they are starting points. Add nodes as the scene requires.
