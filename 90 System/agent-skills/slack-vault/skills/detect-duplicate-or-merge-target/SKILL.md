---
name: detect-duplicate-or-merge-target
description: Use when a newly imported Slack Vault note may duplicate or strongly overlap an existing knowledge note.
---

# Detect Duplicate Or Merge Target

Identify whether an imported knowledge note should remain separate, link to an existing note, or be considered for a later merge.

## Rules

- Do not delete or merge notes during normal connection runs.
- Do not remove source IDs or citations.
- Prefer linking related notes over merging unless the overlap is clearly about the same knowledge object.
- Report merge candidates for the commit gate or operator; do not perform destructive edits.

## Workflow

1. Read the imported note and source record.
2. Search for notes with matching titles, aliases, source topics, customer names, product names, project names, and key entities.
3. Read the most similar candidate notes.
4. Classify each candidate as:
   - `same_object`: likely the same knowledge object;
   - `related_object`: related but should stay separate;
   - `weak_match`: lexical overlap only.
5. For `same_object`, add a conservative related-note link and report a merge recommendation.
6. For `related_object`, add links only when useful.
7. For `weak_match`, make no edits.

## Final Response

Include:

- `Same-object candidates:` list or `None`
- `Related-object links added:` list or `None`
- `Weak matches skipped:` list or `None`
- `Merge recommendation:` concise note for future work
