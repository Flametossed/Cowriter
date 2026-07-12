# Scene Method

> Portable. Draft a single scene from a beat, constrained by the bible (canon) and the craft layer (voice + quality). This is where consistency and quality meet the page.

Fiction's drafting unit — the stack below is the fiction column of [context-map.md](../core/context-map.md). Non-fiction section drafting lives in [nonfiction-method.md](../nonfiction/nonfiction-method.md).

## Load before writing (the context stack)
0. **Brain** — `brain.md` at workspace root ([brain-method.md](../guide/brain-method.md)). Load first; its Efficiency directives may prune items 2–4 below (e.g. "fingerprint locked — skip samples"), and its Writer/Steers lines apply as standing constraints.
1. **The beat** — from `outline.md` (or a one-line ask). What must this scene accomplish?
2. **Bible** — `canon-facts.md` + relevant `characters.md` / `world.md` entries for everyone/everywhere in the scene. Do not contradict a locked fact.
3. **Voice** — `style-fingerprint.md` (if present) → `style-guide.md`. Inject 1–2 short sample excerpts as few-shot when a fingerprint exists.
4. **Quality floor** — `slop-markers.md`, minus this book's allowed exceptions.
5. **Length budget** — the beat's `Tier` + `Budget` from `outline.md` (see [length-method.md](../craft/length-method.md)). Write to the tier as a soft target, not a wall: *"extended scene — give it room, ~2,400 words"* / *"short connective scene — keep it tight, ~900 words."* If no budget is set, draft at the fingerprint's `avg_scene_words`.
6. **Creativity dial** — a 1.0–2.0 knob on how tightly to hew to the loaded constraints. 1.0 = rigid (play everything above safe and literal); 2.0 = max creativity (freest interpretation of beat/voice/canon, still never breaking locked facts). Default **1.2** unless the writer sets otherwise for the session/book. Note the active value when it's not default.

Authority on any conflict: `fingerprint > style-guide > slop-markers`. Canon (bible) is never overridden by style or the creativity dial.

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
- **Sanity check** — before presenting, run a quick inline plausibility pass (the same lens as [continuity-method.md](../revision/continuity-method.md), lighter-weight): does the timeline/chronology hold together, do characters act only on what they currently know, does anything contradict canon, and does the scene make realistic/logical sense on its own terms? Flag anything off rather than silently presenting it.
- **Log the length** — record actual words vs the beat budget in `progress.md` → Length; update the running total and both projections. If the scene drifted from budget materially, surface the reflow choice (hold target / cut a scene / raise target) per [length-method.md](../craft/length-method.md) Step 5 — don't silently re-cap.
- Note any **new facts** invented while drafting (a name, a detail) so `/bible-update` can capture them — list them under the draft. Never let an improvised detail silently become uncatalogued canon.

## Output
Write to `projects/<book>/drafts/`. After the scene, append a short block:
```
--- new facts to log (run /bible-update) ---
- 
```
