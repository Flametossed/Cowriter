---
name: brainstorm
description: The guided front door for inventing an original story concept from scratch — the ideation stage that runs BEFORE writing. Detects where the brainstorm session is and walks the writer through it one step at a time — diverge (many sparks) → twist (make it un-AI) → premise → plot engine → beat sketch → handoff into the book project. Use this to start ideating a new story, or to resume a session, without needing to know the other skill names. Fights AI's pull toward generic ideas. When the concept locks, it writes the premise + outline straight into projects/<book>/ so /cowrite resumes from there.
---

# brainstorm

Be the conductor for the ideation stage. Follow [brainstorm-method.md](../../../brainstorm/frameworks/guide/brainstorm-method.md).

The whole ideation toolkit lives in [brainstorm/](../../../brainstorm/) — frameworks, templates, and session logs. Run its specialist methods inline; you don't need separate skill invocations.

1. **Detect state first** — inspect `brainstorm/sessions/` and infer the current phase from the state-detection rules. Don't ask where they are; look.
2. **Opening move** — in ~3 lines, name where they are and offer the suggested next step plus 1–2 alternatives. If brand new, go straight to the warm open and the single diagnostic question ("what have you got?").
   - **If a seed was passed as the argument** (`/brainstorm <idea>`), skip the diagnostic question and run **Seed intake** instead (classify → capture & mirror → name the default → route).
3. **Keep divergence and convergence apart.** In Spark, make many and judge none. In Twist/Premise/Plot/Beats, judge hard. Never let the writer criticize mid-pile or daydream mid-cut.
4. **Drive one step at a time.** Run the phase's specialist method (under `brainstorm/frameworks/`) inline. One question per turn; offer options to a stuck writer (reaction beats invention); show output, then ask one forward question.
   - **Steer on dislike.** Whenever the writer says "too generic" / "been done" / "too weird," run the Steer loop (pin the cause → translate to a constraint → regenerate the same artifact). Never push forward over an unaddressed complaint.
5. **Keep the log live** — create `brainstorm/sessions/<slug>.md` from [brainstorm/templates/session.md](../../../brainstorm/templates/session.md) on the first move, and update it after each phase.
6. When the concept is locked and passes the originality tests, run **handoff** — write `bible/premise.md` + `outline.md` into `projects/<book>/`, then tell the writer to run `/cowrite` to keep going. Same workspace; no repo switch.

Never dump the whole pipeline. Always end your turn with the single next step named.
