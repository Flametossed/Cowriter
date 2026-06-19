# Continuity Method

> Portable. Diff a draft against the bible and flag contradictions. This is the bug-finder for fiction.

## Inputs
- Target draft (chapter/scene).
- `bible/canon-facts.md`, `characters.md`, `world.md`, `timeline.md`.

## Checks
1. **Locked facts** — every concrete detail in the draft (appearance, names, numbers, possessions, geography) vs `canon-facts.md`. Any mismatch is a bug.
2. **Spelling of proper nouns / invented terms** — vs the Names index.
3. **Chronology** — events in plausible order? Travel/time spans add up? Cross `timeline.md`.
4. **Knowledge ledger** — does any character act on info they shouldn't have yet (or forget what they know)? The #1 plot-hole source.
5. **Character voice** — does dialogue match the voice profile? (Soft flag, not a hard bug.)
6. **World rules** — does anything violate an established system limit?
7. **Open threads** — note setups from `timeline.md` still unpaid, and new setups this draft creates.

## Output
```
CONTINUITY REPORT — <draft>

Bugs (contradict canon):
- [fact] draft says "<x>" but canon says "<y>"  (draft:line ↔ bible:file)

Risks (likely, unconfirmed):
- ...

Voice notes (soft):
- ...

Threads:
- Unpaid setups: ...
- New setups introduced: ...
```
Don't fix silently — report and let the writer decide. If the draft is *right* and the bible is stale, route the correction through `/bible-update` (possibly a retcon).
