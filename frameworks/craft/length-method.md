# Length Method — word budgets, top-down

> Portable. Gives a book a **sense of length** so drafting neither rushes a 90k story into 30k nor bloats it to 150k. The total target is the single source of truth; everything cascades from it. The average scene length is **derived from the style fingerprint** — voice already decides how long scenes run, so length and voice never fight.

> **Compass, not a cage.** Budgets aim the model and raise an alarm on drift. They are never a hard cap — the writer can rebudget any beat, or the whole book, at any time.

---

## Why this exists — the two failure modes

- **Underwriting** — the model summarizes instead of dramatizing. The plot resolves in 30k when it wanted 90k; scenes are compressed to synopsis. A budget that's *higher* than the draft says "this beat is a scene, not a paragraph."
- **Overwriting** — every scene runs long, subplots multiply, 150k for an 80k story. A budget that's *lower* than the draft says "tighten or cut."

Word count is a proxy for **scope discipline**. The budget is what stops scope ballooning in either direction.

---

## Step 1 — Set the total target (Spark / Blueprint)

Set one number, stored in `bible/premise.md` → **Length target**. It becomes a downstream guardrail like *"What this book is NOT"*. Offer a category-aware default so the writer doesn't guess:

| Form | Words |
|------|------:|
| Flash | <1k |
| Short story | 1k–7.5k |
| Novelette | 7.5k–17.5k |
| Novella | 17.5k–40k |
| Novel — general / literary | 70k–100k |
| Novel — debut (safer to sell) | 80k–90k |
| Epic / high fantasy, sci-fi | 100k–150k |
| Romance | 50k–90k |
| Thriller / mystery | 70k–90k |
| Cozy / category romance | 40k–60k |
| Middle grade | 30k–55k |
| YA | 55k–90k |

Pick the midpoint of the chosen band unless the writer names a number. Genre + comps (already in the premise) should nudge it. Record it as a single integer (`90000`), not a range — the cascade needs one number.

---

## Step 2 — Get the average scene length (from the fingerprint)

The avg scene length comes from `style/style-fingerprint.md` → **scene-length** block (`avg_scene_words`), produced by `style-learn`. Voice decides this: spare prose moves in shorter beats, lush prose in longer ones.

- **Fingerprint present** → use its `avg_scene_words`.
- **No fingerprint yet** → fall back to a default by register, and revisit once voice is set:

| Voice | Avg scene |
|-------|----------:|
| spare / minimalist | ~1.2k–1.8k |
| clean / standard | ~2k–2.5k |
| lush / maximalist | ~3k–4k |

This is a **default the writer confirms**, never silently imposed. Surface it: *"Spare voice → ~1.5k scenes → ~60 scenes for 90k. Look right, or set the avg yourself?"*

---

## Step 3 — Cascade total → acts → beats → scenes

Top-down. The writer sets the total; the system derives the rest and proposes it.

1. **Total → acts**, by the chosen structure's proportions. 3-act ≈ **25 / 50 / 25**. Save the Cat, Hero's Journey, etc. have their own — weight by each section's dramatic load, not evenly.
2. **Acts → beats.** Each beat gets a share of its act's budget. **Allocate unevenly on purpose** — climax and midpoint beats are denser; connective beats lean. Don't flatten the curve with an even split.
3. **Beats → scene count.** `scene_count_for_beat = round(beat_budget / avg_scene_words)`. The whole-book scene count falls out of `target / avg_scene_words` (spare 90k → ~60 scenes; lush 90k → ~25). That granularity is *correct craft* — it matches the voice.
4. **Scenes → budget + tier.** Each scene gets a word budget and a tier (below). A turning-point scene takes an `extended` tier from its beat's surplus; connective scenes take `short`.

Write the per-beat `budget` and `tier` into `outline.md`. The cascade is a proposal — the writer nudges any beat, and the rest can reflow (Step 5).

---

## Step 4 — Tiers (what the model actually receives)

LLMs can't hit "2,143 words." They *can* hit a relative size instruction. So a scene's numeric budget maps to a **tier**, and the tier is what `scene-method` puts in front of the model. Track the actual word count against the number; instruct with the tier.

The ladder is **anchored to this book's `avg_scene_words`**, so "extended" means long *for this voice*, not an absolute:

| Tier | Multiple of avg | For |
|------|-----------------|-----|
| micro | ~0.3× | beat, transition, hard cut |
| short | ~0.6× | connective scene, sequel/reflection |
| standard | 1.0× | normal scene |
| extended | ~1.6× | setpiece, midpoint, climax |

So at `avg_scene_words: 1500` → micro ~450, short ~900, standard ~1500, extended ~2400. A spare writer's `extended` ≈ a lush writer's `standard`; every length instruction stays in the writer's own register.

`scene-method` translates the tier to a soft instruction, e.g. *"This is an extended scene — give it room; ~2,400 words is the target, not a wall."*

---

## Step 5 — Track, project, reflow (`progress.md`)

The headline the writer should always see is the **projected final length**. Show two projections:

- **Plan** = `words_written + Σ(remaining scene budgets)`. Equals the target while on plan.
- **Pace** = `(words_written / scenes_done) × total_scenes`. What the current drafting rate extrapolates to.

When **Pace** diverges from **Plan**, that's the alarm — and it fires at 20k, not 60k. Log per scene in `progress.md` → **Length** block: scene actual, running total, % of target, both projections.

**Reflow on drift.** When a scene comes in materially over or under its budget, recompute the *remaining* scene budgets so the total still holds — and offer the choice:

> *"Ch3 ran 1.2k long (3.7k vs 2.5k). Options: (a) hold 90k — remaining 31 scenes rebudgeted −40 words each; (b) cut one connective scene; (c) raise the target to 95k. Which?"*

Never silently re-cap. Reflow is a recalculation the writer approves.

---

## Step 6 — Hand-offs

- **`pacing` (revision)** owns drift *after* drafting. A scene over budget by **>25%** is a pacing flag → trim/cut; a scene under budget that reads as synopsis → expand (it's summary, not a scene). Length drift and tension drift are read together.
- **`outline`** owns the cascade (Step 3) and rebudgeting.
- **`scene`** owns Step 4 — loading a scene's tier and writing to it.
- **`style-learn`** owns Step 2 — deriving `avg_scene_words`.

The whole system hangs off two numbers the writer touches: **total target** (they set) and **avg scene length** (the fingerprint derives). Everything else cascades and can be overridden.
