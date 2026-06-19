---
name: update-vault-maps
description: Use when an imported Slack Vault knowledge note should appear in Obsidian map or index files under 30 Maps.
---

# Update Vault Maps

Maintain readable map files under `30 Maps/` after a new knowledge note is imported.

## Map Files

Common map files include:

- `30 Maps/topic-index.md`
- `30 Maps/project-index.md`
- `30 Maps/product-index.md`
- `30 Maps/customer-index.md`
- `30 Maps/team-index.md`

## Rules

- Keep map files plain Markdown and easy to scan.
- Add a note to an existing section when one clearly fits.
- Create a small new section only when it will likely be reused.
- Do not build a large ontology from a single imported document.
- Use Obsidian wikilinks to knowledge notes.
- Keep entries short: one link plus a concise descriptor when helpful.

## Workflow

1. Read the imported knowledge note metadata and summary.
2. Read relevant map files before editing.
3. Choose at most a few map files that improve navigation.
4. Add the imported note under the best existing heading, or create a minimal heading when needed.
5. Avoid duplicate entries.
6. Report each map file changed.

## Final Response

Include:

- `Map files edited:` list of paths
- `Entries added:` short bullets
- `Maps skipped:` plausible maps skipped with reasons
