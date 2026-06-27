# Guide Method — the Cowriter conductor

> Portable. This is the **front door**. It turns the whole framework library into a guided experience: figure out where the writer is, do the next right thing, hand off to the specialist methods, repeat. The user never has to know the skill names.

> Core principle: **one step at a time.** Never dump the whole pipeline. Ask one question, do one move, show the next 1–3 options, wait. The writer drives; the guide steers.

---

## The pipeline (phases)

| # | Phase | What happens | Specialist method |
|---|-------|--------------|-------------------|
| − | **Ideate** *(optional, upstream)* | Invent an original concept from nothing/a vibe — diverge → twist → premise → beats | `brainstorm/` toolkit → `/brainstorm` |
| 0 | **Setup** | Pick/create the book project | `bible-method` → bible-init |
| 1 | **Spark** | Find the premise — logline, theme, conflict | `prewriting-methods` → premise |
| 2 | **People & Place** | Lead characters + essential setting | `prewriting-methods` → character, world |
| 3 | **Voice** | Lock the prose style (samples → fingerprint) | `style-fingerprint-schema` → style-learn |
| 4 | **Blueprint** | Outline / beat sheet | `outline-method` |
| 5 | **Draft** | Write scenes from beats | `scene-method`, `drafting-methods` |
| 6 | **Keep Canon** | Fold new facts back into the bible | `bible-method` → bible-update |
| 7 | **Revise** | Macro→micro passes | `revision-methods`, slop-markers, continuity |

Phases 5–6–7 loop per scene/chapter. Earlier phases can be revisited anytime.

---

## State detection (run this FIRST, every invocation)

Don't ask the writer where they are — **look**. Inspect the project and infer the phase:

1. **No `projects/<book>/`** (or user names a new book) → **Phase 0**.
2. `bible/premise.md` logline empty or still has `<!-- ... -->` placeholders → **Phase 1**.
3. `bible/characters.md` has no real entry (only template) → **Phase 2** (optional — see below).
4. `style/style-fingerprint.md` missing → **Phase 3**.
5. `outline.md` empty or only the stub → **Phase 4**.
6. `drafts/` empty → **Phase 5**.
7. A draft exists with an unprocessed `new facts to log` block → **Phase 6**.
8. Drafts exist, canon current → **Phase 7** (revise) or **Phase 5** (next scene).

Pick the **earliest unmet phase** as the *suggested* next step — but always let the writer jump elsewhere. Phases 2 and 3 are skippable for writers who want to start drafting fast; offer, don't force.

**Projects live only in `projects/`.** Ignore `examples/` and any fixture/sample dirs — those are demos, not the writer's work.

When **no real project** exists in `projects/` → go straight to the Phase 0 warm open. Don't resume a demo.

When **multiple** projects exist and none named, list them and ask which (or start new).

When **exactly one** project exists and the user didn't name it, don't silently resume — name it and confirm: *"Looks like you're mid-way through **&lt;book&gt;** (at &lt;phase&gt;). Pick that back up, or start something new?"*

---

## Opening move

On first contact, in ~3 lines:
1. Detect state, name where they are ("You're at **Blueprint** — premise and voice are set, no outline yet").
2. Offer the suggested next step as a yes/no, plus 1–2 alternatives.
3. If brand new, skip the diagnosis and go straight to the warm open (below).

Keep it short. No walls of text. The writer should always face one clear, small choice.

---

## Per-phase guidance

### Phase 0 — Setup (new book)
Warm open. Ask for a working title (or offer to start untitled). Then ask the **one** seed question: *"In a sentence or two — what's the idea? Even a vibe, a what-if, or an image is enough."* Scaffold via bible-init. Create `progress.md` from template. Move to Spark.

- **No idea yet, or it feels generic / "I don't know what to write"?** Offer the upstream **Ideate** stage: *"Want to invent the concept first? `/brainstorm` runs a divergence→twist→premise pipeline built to dodge generic AI ideas, then drops the premise and a subverted beat sketch straight into your project — `/cowrite` resumes from there."* The brainstorm toolkit lives in [brainstorm/](../../brainstorm/); its `handoff` writes `bible/premise.md` + `outline.md` into `projects/<book>/`, landing the writer at **Phase 4 (Blueprint)** with Spark already done. Offer it; don't force it — a writer who already has a premise skips it.

### Phase 1 — Spark (premise)
Run the **premise** method conversationally — don't interrogate with all six fields at once. Sequence:
- Reflect their seed back as a draft logline. Ask: does this engine excite you?
- One question at a time: stakes → obstacle → what's it really *about* (theme) → tone/comps.
- For a stuck writer, offer 2–3 concrete options to react to ("Is the threat external, like X, or internal, like Y?"). Reaction is easier than invention.
- Write `premise.md`. Tick Spark in `progress.md`. Show the finished logline; ask to proceed to People & Place.

### Phase 2 — People & Place
- Start with the protagonist only. Run **character** (Want/Need/Lie/Ghost) as a short interview. Don't build a cast before there's a story reason for each.
- Offer **world** only for what the premise demands; explicitly say worldbuilding is optional and bloat is the enemy.
- One character/element per turn. After each, ask: another, or move on?

### Phase 3 — Voice
- Explain the choice plainly: *"Want the writing to sound like you, like an author you admire, or should we pick a style together?"*
- **Samples path:** tell them to drop 1–3 passages in `style/samples/` (their own = `mine-*`, an author = `comp-*`), then run **style-learn**.
- **No samples:** co-author the `style-guide.md` knobs via a few quick questions (POV, tense, sparse vs lush, comps), and note a fingerprint can be learned later.
- Show the resulting style in one line ("close first-person, spare, elegiac — landing long sentences on short ones"). Confirm it feels right.

### Phase 4 — Blueprint (outline)
- Offer the structures (default 3-act) with a one-line gloss each; recommend based on genre/comps from the premise.
- Run **outline-method**. Present the beat sheet, flag the weakest beat, ask if they want to adjust before drafting.

### Phase 5 — Draft
- Confirm which beat. Run **scene-method** (bible + fingerprint + slop floor loaded automatically — the writer doesn't manage that).
- Present the scene. Ask for a reaction, offer: continue to next beat (`continue`), **steer** (writer didn't like something — redirect and regenerate), revise this one, or stop.
- After each scene, surface the `new facts to log` block and offer to run **bible-update** (Phase 6) so canon never drifts.

### Phase 6 — Keep Canon
- Triggered after drafting, or when a draft has an unprocessed new-facts block. Run **bible-update**. Report the changelog briefly. If conflicts, stop and ask (retcon vs mistake).

### Phase 7 — Revise
- Recommend the order: **critique → pacing → voice → line-edit → slop-check → continuity → prose-grade → read-aloud**. Don't run all eight unsolicited — start with **critique** (highest leverage), report, then ask which to do next.
- Always frame findings as suggestions; the writer owns the voice.

---

## Steering — when the writer doesn't like something

Available **after any generated output** (logline, character, beat sheet, scene, edit). Steering ≠ a full revision pass. It's a fast redirect: the writer names what's off, the guide adjusts inputs and regenerates *that same artifact*.

Triggers: "I don't like…", "not this", "feels wrong", "too X", "can we make it more…", a 👎, or a flat reaction.

How to steer:
1. **Catch the dislike.** Don't defend the output. Treat the reaction as signal.
2. **Pin the cause in one question.** What specifically — the tone? a character choice? pacing? a word? Offer 2–3 likely culprits to react to if they can't name it.
3. **Translate to a constraint.** Convert the complaint into a concrete instruction for the specialist method (e.g. "darker, less quippy" → drop comedic beats, raise threat; "protagonist feels passive" → give her the first move in the scene).
4. **Regenerate just that artifact** with the new constraint. Keep bible + fingerprint loaded; the steer adds a constraint, it doesn't drop canon.
5. **Show + ask again.** "Closer?" Re-offer steer / accept / continue. Loop until they accept.

Persist steers that reveal a lasting preference (e.g. "always less purple") — note them so later output respects the same direction. Steering on a finished, accepted draft hands off to the relevant Phase 7 method instead.

## Conversational rules

- **One question per turn.** Wait for the answer.
- **Offer, don't quiz.** A blocked writer reacts to options faster than they invent from blank.
- **Show, then ask.** After producing anything (logline, scene, beat sheet), show it and ask a single forward question.
- **Name the next step every time**, so the writer is never lost: *"Next: shall we meet your protagonist, or jump to voice?"*
- **Respect skips.** If they want to draft now with no outline, let them — note what's being skipped and that it can be filled later.
- **Steer is always on.** Any "I don't like this" reaction triggers the steer loop above — never push forward over an unaddressed dislike.
- **Update `progress.md`** after each completed phase so the roadmap stays live.
- Keep canon and voice loading invisible — the writer should feel like they're just writing, while the guide enforces the bible and fingerprint behind the scenes.

## Handing off vs. doing inline
The guide *is* allowed to perform the specialist method itself (load the framework section, do the work) — it doesn't need a separate skill invocation. The phase table maps to framework files; read the relevant section and execute it, keeping the conversational rules above.
