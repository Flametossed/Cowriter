# Bible Method — building, updating, and querying canon

> Portable. This is the full method for working with a story bible. Paste it into any AI chat, or let the Cowriter skills (`bible-init`, `bible-update`, `bible-check`) drive it.

## What the bible is

A set of plain-Markdown files that hold everything *true* about a book, so any draft can be checked against them and any AI session can be primed with them. Files:

| File | Holds | Checked by |
|------|-------|-----------|
| `premise.md` | logline, theme, conflict, tone | critique, scene |
| `characters.md` | per-character arc, voice, locked details | continuity, dialogue, scene |
| `world.md` | setting, systems, locations, factions | continuity, scene |
| `timeline.md` | event order + knowledge ledger | continuity |
| `canon-facts.md` | flat index of locked atomic facts | continuity, bible-check |

`canon-facts.md` is the authoritative fast-lookup. If a fact is contradiction-prone, mirror it there.

---

## bible-init — scaffold a book

1. Take a book name. Create `projects/<book>/` with:
   - `bible/` ← copy all of `templates/bible/*.md`
   - `style/samples/` (empty, with a `README` telling the user to drop samples)
   - `style/style-guide.md` ← copy `templates/style/style-guide.md`
   - `drafts/`
   - `outline.md` (stub)
2. Replace `{{BOOK_TITLE}}` placeholders with the book name.
3. If the user gave a premise/idea, fill `premise.md` now; otherwise leave the scaffold and point them to `/premise`.
4. Report what was created and the next step.

## bible-update — fold a draft's new canon back in

The most important maintenance loop. Run after drafting.

1. Read the target draft (a chapter/scene file) AND the current bible.
2. Extract every **newly established fact**: appearances, names, places, numbers, relationships, revealed secrets, stated rules, time markers.
3. For each, decide:
   - **New** → add to the right bible file + mirror atomic version into `canon-facts.md`.
   - **Consistent with existing** → no-op.
   - **Contradicts existing** → STOP. Flag it. Do not silently overwrite. Ask the user: is this a mistake in the draft, or a deliberate retcon? On retcon, log it in `canon-facts.md` → Retcon log.
4. Update `timeline.md` (event row + knowledge ledger) for anything that moved the story clock or changed who-knows-what.
5. Output a changelog: Added / Updated / **Conflicts needing a decision**.

> Never invent facts the draft doesn't support. Bible = record, not imagination.

## bible-check — query canon

Answer a question strictly from the bible. Order of lookup: `canon-facts.md` → the topical file → `timeline.md`.
- If the answer is in the bible, give it + cite the file/line.
- If it's **underspecified**, say so plainly and offer to establish it (then route to `bible-update` to record the decision).
- Never guess and never fill a gap silently — an invented "fact" becomes a future continuity bug.
