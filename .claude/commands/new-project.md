# /new-project [name]

Initializes a new Teller project from scratch. Runs the structured node intake defined in `bundles/develop.md`.

## Steps

1. If `[name]` argument provided: use as working title → slugify for `project-id`. If not provided: ask for title first.
2. Confirm: "¿Creamos el proyecto `[name]` en `projects/[slug]/`?"
3. Load `bundles/develop.md`.
4. Run intake Steps 1–6 in order. Do not skip steps.
5. After Step 6 confirmed: scaffold folders + update `CLAUDE.md`.

## Scaffold — folders and seed files to create

```
projects/[slug]/
├── state.md                ← generated in Step 2 of intake
├── characters/
│   └── index.md            ← empty index, one line per character added
├── voice/
│   └── style.md            ← generated in Step 5 of intake
├── system/
│   └── index.md
├── world/
│   └── index.md
├── plot/
│   └── arcs.md             ← generated in Step 6 of intake
├── relations/
│   └── index.md
├── themes/
│   └── index.md
└── chapters/
    └── index.md            ← empty table, filled by session-close after each chapter
```

## CLAUDE.md update

After scaffold complete, edit `CLAUDE.md`:
- Change `Active project: [old]` → `Active project: [slug]`
- Update the two `read:` paths to point to new project's `state.md`

## Notes

- Does not create manuscript files. Manuscript lives outside Teller in user's writing folder.
- Only bible nodes are created here.
- Protagonist node gets `load-with: []` initially — user fills relations and voice links as more nodes are created.
- If project folder already exists: warn user, do not overwrite.
