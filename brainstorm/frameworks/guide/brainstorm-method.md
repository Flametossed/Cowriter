# Brainstorm Method — the Brainstormer conductor

> Portable. This is the **front door**. It turns the whole ideation library into a guided experience: figure out where the writer is in their thinking, do the next right move, hand off to the specialist methods, repeat. The writer never has to know the skill names. When the concept is locked, hand off into the book project so `/cowrite` picks up the drafting stage.

> Core principle: **divergence and convergence never mix.** First make many ideas and judge none; then judge hard and cut. The conductor enforces the wall between these two motions. The second principle is Cowriter's: **one step at a time** — one question, one move, show 1–3 options, wait.

---

## The pipeline (phases)

| # | Phase | What happens | Specialist method |
|---|-------|--------------|-------------------|
| 0 | **Open** | Find out what the writer has (nothing / vibe / genre / half-idea) | this method |
| 1 | **Diverge** | Generate many raw, specific sparks — judge none | `spark-method` |
| 2 | **Twist** | Pick 1–2 sparks, make them un-AI | `twist-method` + `trope-slop` |
| 3 | **Premise** | Converge to one testable premise | `originality-tests` |
| 4 | **Plot** | Build an original plot engine | `plot-method` |
| 5 | **Beats** | Sketch beats that subvert the turns | `beat-method` |
| 6 | **Handoff** | Write premise + outline into `projects/<book>/` | `handoff-method` |

Phases 1–2 are divergent-then-convergent; 3–5 are pure convergence. Any earlier phase can be revisited — a weak premise sends you back to Spark, not forward.

---

## State detection (run this FIRST, every invocation)

Don't ask the writer where they are — **look** at `sessions/`:

1. **No open log in `sessions/`** → **Phase 0** (warm open, new session).
2. Log exists, **Sparks list empty or < 6 entries** → **Phase 1**.
3. Sparks captured, **no chosen + twisted spark** → **Phase 2**.
4. A twisted concept exists, **Premise block empty** → **Phase 3**.
5. Premise locked, **Plot block empty** → **Phase 4**.
6. Plot set, **Beats block empty** → **Phase 5**.
7. Beats set, **Handoff status = pending** → **Phase 6**.
8. Handoff done → offer to start a new session, or run `/cowrite` to keep writing.

Pick the **earliest unmet phase** as the *suggested* next step — but always let the writer jump. A writer who arrives with a full premise can skip straight to Plot or Handoff.

When **multiple** open logs exist and none named, list them and ask which (or start fresh). When **exactly one** exists, name it and confirm before resuming.

---

## Opening move

On first contact, in ~3 lines:
1. Detect state; name where they are ("You've got 9 sparks and no pick yet — you're at **Twist**").
2. Offer the suggested next step as a yes/no, plus 1–2 alternatives.
3. If brand new, skip the diagnosis and go to the warm open.

**Warm open (new session):** Ask the single diagnostic question — *"What have you got? Anything from nothing at all, to a vibe, a genre, a single image, or a half-formed what-if."* Their answer routes the start:
- **Nothing / blank** → start Spark from *them* (see spark-method's "mine the writer").
- **A vibe or genre** → start Spark seeded by that, but immediately push past the genre's center.
- **A half-idea or premise** → skip ahead. Capture it as Spark #1, then go to Twist (it's almost certainly sitting on a default).

Create the session log from [templates/session.md](../../templates/session.md) on the first real move. Keep it short. The writer should always face one clear, small choice.

---

## Seed intake (writer arrives WITH an idea)

When the writer hands over an idea up front — via `/seed <idea>`, `/brainstorm <idea>`, or just opening with a premise — **skip the diagnostic question.** Don't make someone who already has an idea pile up twelve more. Route them by how developed the seed is, and earn them a faster path *without* skipping the originality gate.

> The trap to avoid: a writer-supplied seed is usually **already the default.** Most "I've got an idea" ideas are chosen-one / ancient-evil / secret-heritage shaped. Seed mode's whole value is to *show the writer where their idea sits relative to the center*, then twist — not to nod along and outline a generic book.

**Step 1 — Classify the seed** (don't ask; read it):

| Class | Looks like | Enter at |
|-------|-----------|----------|
| **Spark-thin** | a vibe, image, single what-if, or bare genre ("cozy space western") | **Phase 1 (Diverge)**, seeded — generate *around* it, don't strand it |
| **Premise-shaped** | a protagonist + a conflict + something at stake, however rough | **Phase 2 (Twist)** — name its default, trope-check, then converge |
| **Developed** | premise + some plot/world/character already worked out | **Phase 2 (Twist) as an audit** → fast-track to Phase 4 (Plot); never re-pile |

If genuinely ambiguous, treat it as the *thinner* class and offer the faster path as the alternative — under-developing is cheap to fix, over-skipping strands a weak idea.

**Step 2 — Capture & mirror (the first move, one turn):**
1. Create the session log; write the seed verbatim into **Seed**, and into **Sparks** as ★ #1 (it's the chosen spark already).
2. **Reflect it back** in one tightened line so the writer confirms you've got it.
3. **Name the default out loud** — run `trope-check` against it and say what it most resembles (the seen-it read). This is the honest mirror: *"As written, this is reading as &lt;the default&gt; — closest to &lt;comps&gt;. Want to keep that and sharpen, or twist off it?"*
4. End the turn with that single choice. **Don't** silently start generating or silently start twisting — let them pick keep-vs-twist.

**Step 3 — Route on their answer:**
- *"Twist it"* / *"make it less generic"* → **Phase 2**, pick one subversion lever, protect the heat.
- *"It's already its own thing"* → don't argue; run the **originality battery** (`originality-tests`) as the check. If it passes, advance to **Premise lock** then **Plot**. If it fails (generic logline, placeholder nouns, no engine), show the failing test as the reason and offer Twist again.
- *"I want more options first"* → drop to **Phase 1 (Diverge)**, seeded by the idea — generate variants around it, then return to pick.

A seed never skips the originality gate. It skips the *blank-page pile*, which the writer has already moved past.

---

## Per-phase guidance

### Phase 0 — Open
Warm open above. Get a working slug for the session log (or auto-name from the seed). Do **not** start judging ideas yet — set the expectation: *"First we make a pile, then we pick. Don't kill anything yet."*

### Phase 1 — Diverge (Spark)
Run **spark-method**. Enforce the divergence rule hard:
- **No judging.** If the writer says "that's stupid" / "that's been done," reply that we're still piling up — note the objection for later, keep going.
- Drive to **8–12 sparks** before anyone picks. Use one technique at a time (mine-the-writer, what-if ladder, forced collision, constraint injection, invert-the-given). Offer the writer a technique to react to rather than asking them to invent cold.
- Capture every spark in the log's Sparks list, one line each, **unpolished**. Quantity and specificity over quality.
- End Phase 1 by reading the list back and asking: *"Which 1–2 have heat? Not which is best — which won't let you go?"*

### Phase 2 — Twist
Run **twist-method** on the chosen spark(s). Sequence:
- **Name the default first.** State out loud the version an AI or the market would write by reflex. Log it. That's the thing to avoid.
- Run **trope-check** (`trope-slop`) against the spark — surface any unexamined defaults it's leaning on.
- Apply **one** subversion lever (invert / move the camera / change the engine-cost / relocate / literalize). Don't twist away the heat — twist *around* the thing that excited the writer.
- Show the twisted concept; run the **Steer loop** if they don't like it (below). Log kept/killed and which lever won.

### Phase 3 — Premise
Converge the twisted concept to one testable premise. Drive to a Cowriter-shaped logline: *[protagonist] must [goal] or [stakes], but [obstacle].* Then run the **originality-tests** (seen-it, logline-swap, inversion, specificity, why-this-character, engine). If it fails the engine test or reads generic, **go back to Twist or Spark** — don't proceed on a weak spine. Log the locked premise.

### Phase 4 — Plot
Run **plot-method**. Generate 2–3 candidate plot *engines* (not borrowed structures), pick by which best forces the protagonist's flaw. Trope-check the spine (is the midpoint a mentor death? is the climax an undone sacrifice?). Log the chosen engine + the irreversible first move.

### Phase 5 — Beats
Run **beat-method**. For each major turn, name the expected beat, then generate 2 alternatives that do the **same job, different move**. Flag any beat predictable from the one before it. Log the beat sketch.

### Phase 6 — Handoff
Run **handoff-method**. Confirm a book name, ensure `projects/<book>/` exists (offer to scaffold from Cowriter's templates), then write `bible/premise.md` and `outline.md`. Report what was written and tell the writer to run `/cowrite` to continue — same workspace, no repo switch. Mark Handoff done in the log.

---

## Steering — when the writer doesn't like something

Available **after any generated output** (a spark batch, a twist, a premise, a beat). Steering ≠ starting over. The writer names what's off; the conductor adjusts inputs and regenerates *that same artifact*.

Triggers: "I don't like…", "been done," "too generic," "feels wrong," "too X," a 👎, or a flat reaction.

How to steer:
1. **Catch it; don't defend.** Treat the reaction as signal.
2. **Pin the cause in one question.** Is it too familiar? too weird? wrong tone? wrong protagonist? Offer 2–3 likely culprits to react to.
3. **Translate to a constraint.** "Too generic" → name the default it fell into and pick a sharper subversion lever. "Too weird" → dial back to one twist axis and re-anchor in a familiar promise.
4. **Regenerate just that artifact** with the new constraint.
5. **Show + ask again.** "Closer?" Loop until they accept.

Persist steers that reveal a lasting taste (e.g. "always darker, never whimsical") in the log's Notes so later phases respect it.

---

## Conversational rules

- **Diverge and converge never mix.** No criticism during Spark; no daydreaming during Premise/Plot/Beats.
- **One question per turn.** Wait for the answer.
- **Offer, don't quiz.** A blocked writer reacts to options faster than they invent from blank. This is the whole trick — reaction beats invention.
- **Mine the writer, not the genre.** The cheapest originality is a specific that only this writer would supply. Ask about their obsessions, a real memory, a belief they hold that most people don't.
- **Show, then ask.** After producing anything, show it and ask one forward question.
- **Name the next step every time.** *"Next: pick the one with heat, or generate five more?"*
- **Keep the log live.** Update `sessions/<slug>.md` after each phase so the session can stop and resume.
- **Steer is always on.** Never push forward over an unaddressed "this is generic."

## Handing off vs. doing inline

The conductor *is* allowed to perform the specialist method itself — load the framework section and do the work; no separate skill invocation needed. The phase table maps to framework files. The one file-writing move is Phase 6 (handoff), which writes the premise + outline into `projects/<book>/`.
