---
name: connect-imported-document
description: Use after Slack Vault imports and synthesizes a source document into a knowledge note, to connect that note to related Obsidian vault notes and map files.
---

# Connect Imported Document

Connect a newly imported Slack Vault knowledge note into the existing Obsidian graph.

## Inputs

The orchestration prompt should provide:

- Vault path
- Source ID
- Source record path
- Primary knowledge note path
- Allowed edit folders
- Any configured edit limits

## Boundaries

- Edit only Markdown inside the allowed vault folders provided by orchestration.
- Do not run Git commands.
- Do not edit `.obsidian/`, `.git/`, archives, logs, SQLite databases, Slack downloads, or original source files.
- Do not edit `90 System/agent-skills/**` during normal connection runs.
- Preserve source citations and the `## Sources` section in generated knowledge notes.
- Do not invent facts. New prose must be grounded in the imported note, source record, or existing vault notes.
- Prefer useful, sparse links over dense linking.

## Workflow

1. Read the primary knowledge note and source record fully.
2. Identify useful search terms from the title, topics, taxonomy, named entities, teams, tools, customers, products, projects, and source filename.
3. Search the vault for related notes and map files.
4. Read the most relevant candidate notes before editing.
5. Add wikilinks where the imported note already mentions an existing concept.
6. Add or update a `## Related Notes` section when it improves navigation.
7. Update relevant `30 Maps/*-index.md` files with a link to the imported note.
8. Add reciprocal links only when the relationship is clear from existing text.
9. Run the `verify-vault-links` workflow before finishing when available.
10. Report every file edited and a short reason for each edit.

## Editing Guidance

Good connection edits include:

- Linking an imported HubSpot note to an existing sales operations note when both discuss the same operating area.
- Adding a product operating model note to `30 Maps/topic-index.md` or another relevant map file.
- Adding a short related-note bullet that explains the relationship in one sentence.

Avoid:

- Rewriting a note just to improve style.
- Creating a new taxonomy from one document.
- Adding links to every repeated noun.
- Creating bridge notes unless orchestration explicitly enables that mode.

## Final Response

End with:

- `Edited files:` list of vault-relative paths
- `Connections added:` concise bullets
- `Skipped candidates:` any plausible links intentionally skipped
- `Validation notes:` anything the commit gate should pay attention to
