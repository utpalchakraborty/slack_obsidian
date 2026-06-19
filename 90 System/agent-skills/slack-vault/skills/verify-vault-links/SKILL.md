---
name: verify-vault-links
description: Use after editing Slack Vault Obsidian notes to check that wikilinks are intentional and resolvable.
---

# Verify Vault Links

Audit wikilinks in files edited during a connection run.

## Rules

- Obsidian wikilinks should point to existing notes unless the text is intentionally a plain-text forward reference.
- Prefer piped links when the target filename is not natural reading text: `[[target-note|Display Name]]`.
- Image embeds such as `![[image.png]]` are outside the connection workflow and should not be changed.
- Do not create placeholder notes just to satisfy a link.
- Do not edit `90 System/agent-skills/**` during normal connection runs.

## Workflow

1. Inspect every edited Markdown file.
2. List all `[[wikilinks]]` that were added or changed.
3. Confirm each target resolves to an existing Markdown note by path, filename stem, title, or alias.
4. For unresolved concepts, either remove the wikilink and leave plain text, or link to the best existing note if one clearly matches.
5. Report unresolved links that remain intentionally as validation notes.

## Final Response

Include:

- `Checked files:` list of paths
- `Resolved links:` count or short list
- `Unresolved links:` list, or `None`
