---
name: bible-init
description: Scaffold a new long-form fiction project — creates projects/<book>/ with a full story bible, style folder, and drafts dir from the templates. Use when starting a new book.
---

# bible-init

Scaffold a new book project.

1. Get the book name from the argument (kebab-case it for the folder; keep the display title for `{{BOOK_TITLE}}`).
2. Follow the **bible-init** section of [bible-method.md](../../../frameworks/bible/bible-method.md).
3. Source templates: [templates/bible/](../../../templates/bible/) and [templates/style/style-guide.md](../../../templates/style/style-guide.md).
4. Replace every `{{BOOK_TITLE}}` with the display title.
5. If the user supplied a premise/idea in the args, fill `premise.md`; else leave the scaffold.

After scaffolding, report the created tree and tell the user the next steps: drop samples into `style/samples/`, run `/style-learn`, then `/premise`.
