---
name: handoff
description: Package the locked concept — premise, plot engine, beat sketch — into Cowriter's bible format and write it into projects/<book>/, so the writer can run /cowrite and continue into characters, voice, and drafting. Use when the concept is locked and has passed the originality tests. Maps the rejected defaults into Cowriter's "What this is NOT" guardrails.
---

# handoff

Bridge from the ideation stage into the book project. Follow [handoff-method.md](../../../frameworks/handoff/handoff-method.md).

1. **Check preconditions** — premise locked + passed `originality-tests`, plot engine exists, beat sketch exists (recommended). If soft, route back; don't paper over a weak spine.
2. **Name & scaffold** — kebab-case the title; if `projects/<book>/` is missing, scaffold from Cowriter's templates (mirror `bible-init`); if it exists with real content, ask before overwriting.
3. **Map into `bible/premise.md`** — fill every Cowriter field from the session log. Put the **rejected defaults** (from `twist`) into **"What this book is NOT"** — they become Cowriter's downstream guardrails.
4. **Map the beat sketch into `outline.md`** — one block per subverted turn; leave structure choice to Cowriter unless already chosen.
5. **Report & redirect** — show the tree written, then tell the writer to run `/cowrite` in the same workspace. Mark Handoff = done in the log.
