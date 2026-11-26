# Domain Docs

How the engineering skills should consume this repo's domain documentation when exploring the codebase.

## Layout: single-context

This repo is **single-context**: one `GLOSSARY.md` at the repo root covers the whole repo, and architecture decisions live in `docs/adr/`. Do not create `GLOSSARY-MAP.md` or per-context glossaries and ADR directories unless the repo actually splits into separate contexts.

The old `CONTEXT.md` / `CONTEXT-MAP.md` names are retired. Only `GLOSSARY.md` and `GLOSSARY-MAP.md` are recognized.

## Before exploring, read these

- **`GLOSSARY.md`** at the repo root. If the repo ever becomes multi-context, also read **`GLOSSARY-MAP.md`** and each `GLOSSARY.md` it points at.
- **`docs/adr/`**: read ADRs that touch the area you're about to work in.

If any of these files don't exist, **proceed silently**. Don't flag their absence; don't suggest creating them upfront. The `/domain-modeling` skill (reached via `/grill-with-docs` and `/improve-codebase-architecture`) creates them lazily when terms or decisions actually get resolved.

## File structure

Single-context repo (this repo):

```
/
├── GLOSSARY.md
├── docs/adr/
│   ├── 0001-event-sourced-orders.md
│   └── 0002-postgres-for-write-model.md
└── src/
```

## Use the glossary's vocabulary

When your output names a domain concept (in an issue title, a refactor proposal, a hypothesis, a test name), use the term as defined in `GLOSSARY.md`. Don't drift to synonyms the glossary explicitly avoids.

If the concept you need isn't in the glossary yet, that's a signal: either you're inventing language the project doesn't use (reconsider) or there's a real gap (note it for `/domain-modeling`).

## Flag ADR conflicts

If your output contradicts an existing ADR, surface it explicitly rather than silently overriding:

> _Contradicts ADR-0007 (event-sourced orders), but worth reopening because…_
