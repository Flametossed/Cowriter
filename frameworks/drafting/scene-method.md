# Scene Method

> Portable. Draft a single scene from a beat, constrained by the bible (canon) and the craft layer (voice + quality). This is where consistency and quality meet the page.

## Load before writing (the context stack)
1. **The beat** — from `outline.md` (or a one-line ask). What must this scene accomplish?
2. **Bible** — `canon-facts.md` + relevant `characters.md` / `world.md` entries for everyone/everywhere in the scene. Do not contradict a locked fact.
3. **Voice** — `style-fingerprint.md` (if present) → `style-guide.md`. Inject 1–2 short sample excerpts as few-shot when a fingerprint exists.
4. **Quality floor** — `slop-markers.md`, minus this book's allowed exceptions.
5. **Length budget** — the beat's `Tier` + `Budget` from `outline.md` (see [length-method.md](../craft/length-method.md)). Write to the tier as a soft target, not a wall: *"extended scene — give it room, ~2,400 words"* / *"short connective scene — keep it tight, ~900 words."* If no budget is set, draft at the fingerprint's `avg_scene_words`.

Authority on any conflict: `fingerprint > style-guide > slop-markers`. Canon (bible) is never overridden by style.

## Scene scaffold (decide before prose)
- **Goal:** what does the POV character want in this scene?
- **Conflict:** what's in the way?
- **Turn:** the value flips (+→− or −→+). A scene with no turn is a description, cut or merge it.
- **Exit on a hook:** end on change, question, or escalation.
- **POV + tense:** per style-guide; one POV per scene unless the book's rule says otherwise.

## Drafting rules (the quality contract)
- Enter late, leave early. Skip the throat-clearing.
- Show via body/action/concrete detail; obey the filter-word and named-emotion bans in `slop-markers.md`.
- Specific ownable detail over generic atmosphere.
- Vary sentence length and openers on purpose.
- Dialogue carries subtext; don't explain it after.
- Honor each character's voice profile from the bible.

## After drafting
- Self-check against `slop-markers.md`; clean obvious tells before presenting.
- **Log the length** — record actual words vs the beat budget in `progress.md` → Length; update the running total and both projections. If the scene drifted from budget materially, surface the reflow choice (hold target / cut a scene / raise target) per [length-method.md](../craft/length-method.md) Step 5 — don't silently re-cap.
- Note any **new facts** invented while drafting (a name, a detail) so `/bible-update` can capture them — list them under the draft. Never let an improvised detail silently become uncatalogued canon.

## Output
Write to `projects/<book>/drafts/`. After the scene, append a short block:
```
--- new facts to log (run /bible-update) ---
- 
```
