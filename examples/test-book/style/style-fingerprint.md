# Style Fingerprint — The Lamplighter's Daughter
Source samples: mine-01.md   Mode: match-mine

## Metrics
- Avg sentence length: ~14 words (range 3–34, **high variance: yes** — deliberate)
- Avg paragraph length: ~3 sentences
- Dialogue ratio: ~0% in sample (interior-led narration)
- Fragment usage: occasional, controlled ("Two taps, a drag.")
- Em-dash / semicolon frequency: low; commas do the work of accretion

## Voice
- POV + tense: first person, past tense
- Narrative distance: deep interiority, confessional
- Register (1 plain – 5 ornate): 2.5 — plain words, weighted by rhythm not vocabulary
- Tone: elegiac, hushed, grief held at arm's length by understatement

## Signature moves (DO)
- Short declarative after a long flowing sentence, as a landing ("I did not wave.")
- Self-correction / second-guessing as characterization ("Some nights I told myself… Other nights I knew it for what it was")
- Concrete domestic objects carrying emotion (the trimmed wick, the dented brass)
- Aphoristic one-liners stated flat ("You learn not to wave.")
- Sound as off-screen information (the cane: "Two taps, a drag.")
- Personified fog/dark, but restrained — one image, not a pile

## Diction
- Favored vocabulary: plain Anglo-Saxon nouns; almost no Latinate abstraction
- Metaphor style: sparing, one per beat, concrete vehicle ("fear wearing love's coat")
- Sensory channels favored: sight (flame/fog) + sound (cane); little smell/taste

## Avoids (DON'T)
- No adverbial dialogue tags (no dialogue at all here)
- No purple atmosphere words (no "palpable," "crackled")
- No named emotions — grief is shown through objects and refusal to act
- No triads / list-of-three rhythm

## slop-marker reconciliation
> Where this voice intentionally breaks the generic slop floor — `slop-check` MUST respect these:
- **Fragments are intentional** ("Two taps, a drag.") — do not flag.
- **Personified setting** (fog "feeling for the windows") is a signature, used sparingly — allow one per scene, flag only if it clusters.
- **Sentence-opening "I"** recurs by design of first-person confessional — flag only true monotony runs (4+).

## Paste-ready style prompt
> Write in close first-person past tense, confessional and elegiac. Use plain, concrete nouns over ornate vocabulary; let rhythm carry weight. Vary sentence length sharply — land long, flowing sentences with a short declarative. Show grief through domestic objects and the refusal to act, never by naming the emotion. Allow sparing personification of fog and dark (one image per scene). Use aphoristic flat one-liners. Avoid adverbial dialogue tags, purple atmosphere words, and rhythmic triads.
