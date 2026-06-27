# Trope Slop — the idea kill-list

> Portable quality floor for *ideas*, the concept-level analog of Cowriter's [slop-markers](../../../frameworks/craft/slop-markers.md). A catalog of the story moves AI (and the market average) reaches for by reflex, each with **detection** and **fix**. Paste it into any chat as a "is my idea defaulting?" block, or let `trope-check` scan a premise/plot/beat against it.

> **Authority:** this is the *floor*, the lowest-priority rule set. A trope is **not** slop. The *unexamined default* is. If the writer reaches for a trope **knowingly, with a genuine new angle**, intent wins — do not flag it. Order: `writer's intent > fresh angle > trope-slop`. Flag the reflex, not the trope.

---

## How to use this

A trope earns its place when it passes **two gates**:
1. **Awareness** — the writer named it as the default (see `twist-method` step 1).
2. **Angle** — at least one load-bearing axis is genuinely twisted (`twist-method` step 2).

Flag only tropes that pass *neither* gate — they're load-bearing on familiarity alone. For each, give the writer the *opening*, not a verdict; they own the choice.

---

## 1. Premise spines (highest priority — kill on sight if unexamined)

- **The Chosen One / prophecy** — a special individual destined to save the world.
  - *Why slop:* the single most predicted fantasy spine; collapses agency into fate.
  - *Fix:* refuse it, fulfill it early, make the prophecy wrong/weaponized, or follow the *un*-chosen.
- **Ancient evil reawakens** — a sealed dark force stirs after centuries.
  - *Fix:* make the "evil" have a reasonable grievance, or make the *sealing* the crime.
- **Secret special heritage** — orphan is secretly royal / last of a bloodline / has rare power.
  - *Fix:* make the heritage a liability, a lie, or irrelevant to the actual problem.
- **The reluctant hero dragged into destiny** — ordinary person pulled from a quiet life.
  - *Fix:* let them *want* in, for a flawed reason; or let someone eager be the wrong choice.
- **Hidden magical world the protagonist secretly belongs to** — the masquerade / "you're a wizard."
  - *Fix:* what if they're told and it's *boring*, or bureaucratic, or already dying?
- **The Empire vs. the plucky Rebellion** — monolithic evil regime, scrappy good resistance.
  - *Fix:* the rebellion won and must now govern badly; or the empire is the lesser evil.
- **It was all a dream / simulation / they were dead the whole time** — the reality rug-pull.
  - *Why slop:* retroactively voids the stakes; an ending that costs the reader their investment.
  - *Fix:* almost always cut. If kept, the reveal must *raise* stakes, not dissolve them.
- **Amnesiac protagonist piecing together their identity.**
  - *Fix:* they remember everything and that's the problem; or the forgotten thing is mundane.

## 2. Plot turns (the default beats)

- **The mentor dies at the midpoint** — the Obi-Wan / Gandalf-falls beat.
  - *Fix:* mentor lives and becomes an obstacle; or was never wise; or the *student* fails them.
- **Betrayal-reveal as the midpoint twist** — the trusted ally was a plant.
  - *Fix:* the "betrayal" is a misread; or the betrayer is right; or no one betrays anyone and the threat is structural.
- **Self-sacrifice that gets undone** — hero dies heroically, then is resurrected/saved.
  - *Why slop:* wants the emotion of death without the cost. Pick one.
  - *Fix:* the sacrifice sticks, or the rescue has a price worse than the death.
- **The power of love/friendship literally wins** — a bond overrides the rules at the climax.
  - *Fix:* the bond *costs* something to use, or fails, or wins the wrong thing.
- **The final-boss duel** — climax collapses to a one-on-one fight.
  - *Fix:* let the climax be a *choice* or a *cost*, not a combat; the engine should dictate it.
- **Fridging** — a loved one killed to motivate the protagonist.
  - *Fix:* give the dead person their own agency *before* death, or motivate without a corpse.
- **The villain explains the plan** — monologue exposition at gunpoint.
  - *Fix:* reveal through action; or the villain is wrong about their own plan.

## 3. Villain defaults

- **Wants to watch the world burn / evil for evil's sake** — motiveless chaos.
- **The genocidal balance-keeper** — "I must wipe out half to save the rest" (the Thanos).
- **Tragic-backstory-explains-everything** — one trauma fully accounts for the villainy.
  - *Fix:* a villain whose logic the reader half-agrees with; motive ≠ excuse.
- **The protagonist's literal dark mirror** — "we're not so different, you and I."

## 4. Character / cast defaults

- **Trauma backstory as the whole personality** — the Ghost *is* the character.
  - *Fix:* let the wound shape them sideways, not define them; give competing drives.
- **The ragtag found family** — fine and beloved, but flag when it's the *default* ensemble with the stock roles (the gruff one, the comic relief, the wise old one).
- **Love triangle as the emotional engine** — two suitors, one choice.
- **The Strong Female Character™** — competence as a substitute for interiority.
- **Chosen-one's wise old mentor** — exposition with a beard.

## 5. Setting / texture tells

- **Generic medieval-European fantasy kingdom** — taverns, kings, a map with a Dark Land in the corner.
  - *Fix:* one specific organizing rule the setting actually runs on (economy, ecology, taboo).
- **The dystopia run by a single evil corporation/government** with no economics behind it.
- **The quaint small town with a dark secret.**
- **Post-apocalypse as aesthetic** — ruins for mood, with no logic of survival.

## 6. Naming & logline tells (surface slop — quick to detect)

- **Fantasy names with apostrophes / doubled vowels** for "exotic" — *Kael'thas, Aer'in*.
- **"The [Adjective] [Noun]" title reflex** — *The Shattered Crown, The Broken Throne, The Crimson Oath*.
- **Logline openers that signal default shape:** *"In a world where…"*, *"...must learn to…"*, *"the only one who can stop…"*, *"little did they know…"*, *"everything changed when…"*.
  - *Fix:* if the logline fits a dozen existing books, the premise underneath is probably centered too — send it back to `twist-method`.

---

## How `trope-check` should report

For each flagged element:
```
[category] "the defaulting element"
  default: <the reflex it's leaning on>
  gates: awareness <pass/fail> · angle <pass/fail>
  opening: <one concrete subversion direction — not a verdict>
```
End with an **originality read**: how many *load-bearing* elements are unexamined defaults, and the single highest-leverage twist to make. Don't rewrite the concept — flag + open the door, and let the writer keep authorship. A concept that fails many markers isn't bad; it's *un-twisted* — route it back to `twist-method`.
