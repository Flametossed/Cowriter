# Style Fingerprint — schema + method

> How to turn raw writing **samples** into a measurable, paste-ready style spec. Used by `style-learn`. Output is written to `projects/<book>/style/style-fingerprint.md`.

> **Authority:** the fingerprint is the *top* of the stack. Where it conflicts with `style-guide.md` or `slop-markers.md`, the fingerprint wins — it's evidence of how the target voice actually behaves.

## Inputs
- Everything in `projects/<book>/style/samples/`.
- Each sample's **mode**, if labeled: `match-mine` (the user's own prose) or `emulate-comp` (an admired author).
  - For `emulate-comp`: extract **technique and patterns**, never reproduce text. The goal is to write *like*, not to copy.

## Method
1. Read all samples. If mixed authors/modes, note it; don't blend incompatible voices — ask which to prioritize.
2. Measure, don't vibe. Where possible give numbers + a representative quote.
3. Separate **signature** (do this) from **avoids** (never do this).
4. **Derive the scene-length tendency** (see below) — voice decides how long scenes run; the length system reads this.
5. Write the fingerprint using the schema below.

## Deriving the scene-length block
This feeds [length-method.md](length-method.md): the average scene length is a property of the voice, not a separate guess. Fill `avg_scene_words` and `tendency`:

- **Measured** (`derived_from: measured`) — if samples contain whole scenes with breaks, measure actual scene word counts and average them. Highest confidence.
- **Inferred** (`derived_from: inferred`) — usual case (samples are passages, not full scenes). Read the prose-density signals you already measured (sentence/paragraph length, description load, interiority, register) and map to a tendency:

  | Voice | tendency | avg_scene_words |
  |-------|----------|----------------:|
  | spare / minimalist (short sentences, white space, little description) | spare | ~1.2k–1.8k |
  | clean / standard (most commercial prose) | standard | ~2k–2.5k |
  | lush / maximalist (long sentences, dense description, heavy interiority) | lush | ~3k–4k |

Inferred is a **default the writer confirms at Blueprint**, never silently imposed. Set `confidence` honestly (`low`/`medium`/`high`).

## Output schema → `style-fingerprint.md`

```markdown
# Style Fingerprint — {{BOOK_TITLE}}
Source samples: <list>   Mode: match-mine | emulate-comp | mixed

## Metrics
- Avg sentence length: <n> words (range <lo>–<hi>, high variance? y/n)
- Avg paragraph length: <n> sentences
- Dialogue ratio: ~<n>% of text
- Fragment usage: none | occasional | frequent
- Em-dash / semicolon frequency: <per 1000 words>

## Scene length
<!-- Feeds length-method.md. Voice sets how long scenes run. -->
- avg_scene_words: <n>
- tendency: spare | standard | lush
- derived_from: measured | inferred
- confidence: low | medium | high

## Voice
- POV + tense: <...>
- Narrative distance: <...>
- Register (1 plain – 5 ornate): <n>
- Tone: <...>

## Signature moves (DO)
- <pattern> — e.g. "opens scenes mid-action", "concrete nouns over adjectives"
- ...

## Diction
- Favored vocabulary / tics: <words>
- Metaphor style + frequency: <...>
- Sensory channels favored: <sight/sound/touch/...>

## Avoids (DON'T)
- <patterns absent from the samples — e.g. "no adverbial dialogue tags">

## slop-marker reconciliation
<!-- Which generic slop-markers this voice intentionally violates → slop-check must respect these. -->
- 

## Paste-ready style prompt
<!-- A tight paragraph the writer can drop into any AI as a system/style instruction. -->
> 
```

## Maintenance
Re-run `style-learn` when samples are added/changed. The fingerprint is regenerated, not hand-edited — manual tweaks belong in `style-guide.md`.
