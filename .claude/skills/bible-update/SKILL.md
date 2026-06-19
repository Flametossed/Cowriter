---
name: bible-update
description: Read a draft (chapter/scene) and fold its newly established facts back into the story bible — adds new canon, updates timeline/knowledge-ledger, and flags contradictions instead of overwriting. Use after drafting.
---

# bible-update

Maintain the bible from a freshly written draft.

1. Identify the target draft file (from args, or the most recent file in `projects/<book>/drafts/`) and the book's `bible/`.
2. Follow the **bible-update** section of [bible-method.md](../../../frameworks/bible/bible-method.md).
3. Extract newly established facts; route each to the correct bible file and mirror atomic facts into `canon-facts.md`.
4. Update `timeline.md` (events + knowledge ledger).
5. **Contradictions: stop and ask** — never silently overwrite canon. Retcons go in the Retcon log.

Output a changelog grouped: **Added / Updated / Conflicts needing a decision.**
