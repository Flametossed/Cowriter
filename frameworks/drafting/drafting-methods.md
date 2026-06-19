# Drafting Methods — expand, continue, dialogue

> Portable. Three drafting moves that build on [scene-method.md](scene-method.md). All load the same **context stack** — bible (canon) + voice (`style-fingerprint` → `style-guide`) + quality floor (`slop-markers` minus this book's exceptions). Authority on conflict: `fingerprint > style-guide > slop-markers`; canon is never overridden by style. All append a `new facts to log` block for `/bible-update`.

---

## expand

Turn a single outline beat into prose. The bridge from `outline.md` to a draft.

1. Pull the beat from `outline.md`: its purpose, the value-turn it must deliver, what it sets up / pays off.
2. Decide the unit: one beat may be one scene or several. Don't pad a thin beat into a long scene — if there's not enough conflict, say so and suggest merging or cutting.
3. Build each scene with the scene scaffold (goal / conflict / turn / hook), then draft per the quality contract in scene-method.
4. Keep the beat's **turn** intact — the prose must land the value shift the outline promised, or the outline and draft have diverged (flag it).

Output: scene file(s) in `drafts/`, each ending with the new-facts block.

---

## continue

Extend an in-progress draft from where it stopped — without losing voice or canon.

1. Read the **tail** of the existing draft (last scene or two) for momentum, voice, and the open dramatic question.
2. Load the context stack. Crucially, read `timeline.md` → **knowledge ledger**: what does each present character know *as of this moment*? Don't let them act on info they don't have yet.
3. Identify the live hook the previous text left on, and the next beat from `outline.md`.
4. Draft forward. Match the established rhythm of *this draft*, not a generic version of the style — sample the preceding paragraphs as the immediate voice reference.
5. Don't recap what just happened; trust continuity.

Output: appended prose + new-facts block. If the next beat is unclear, stop and ask rather than inventing plot.

---

## dialogue

Generate or sharpen an exchange so each line is in-voice and load-bearing.

1. Load every speaker's **voice profile** from `bible/characters.md` (rhythm, vocabulary, tics, what they refuse to say, sample line).
2. Set the scene's dramatic frame: what does each party *want* in this conversation, and what are they hiding? Dialogue is conflict, not information transfer.
3. Draft so that:
   - Each character is identifiable by voice with tags stripped — if you can't tell who's speaking, the voices aren't distinct yet.
   - Subtext carries the weight; **do not** follow a line with prose explaining what it meant.
   - Tags obey the style-guide (default plain "said" / action beats; no adverb-propped tags unless the style allows).
   - At least one **turn** happens — someone's position, power, or knowledge shifts.
4. For a sharpen pass on existing dialogue: flag on-the-nose lines, exposition dumps, and voice bleed (two characters sounding the same); rewrite only the flagged lines, preserving the writer's intent.

Output: the exchange (+ new-facts block if anything new is established).
