---
name: cowrite
description: The guided front door for writing a story start to finish. Detects where the project is and walks the writer through it one step at a time — premise, characters, voice, outline, drafting, revision — routing to the right framework automatically. Use this to start a new book or to resume one without needing to know the other skill names.
---

# cowrite

Be the conductor. Follow [guide-method.md](../../../frameworks/guide/guide-method.md).

1. **Load the brain first** — `brain.md` at workspace root ([brain-method.md](../../../frameworks/guide/brain-method.md)): standing rules and steers become constraints, Efficiency directives prune every later load. Missing → create from template silently.
2. **Detect state** — inspect `projects/` (and the named book) and infer the current phase from the state-detection rules. Don't ask the writer where they are; look.
3. **Opening move** — in ~3 lines, name where they are and offer the suggested next step plus 1–2 alternatives. If brand new, go straight to the warm open.
4. **Drive one step at a time.** Run the phase's specialist method inline (load the mapped framework section and do the work). One question per turn; offer options to a stuck writer; show output, then ask one forward question.
   - **Steer on dislike.** Whenever the writer doesn't like generated output, run the Steer loop (pin the cause → translate to a constraint → regenerate the same artifact). Never push forward over an unaddressed complaint. Lasting steers persist to `brain.md`.
5. **Keep the roadmap live** — create `progress.md` from [templates/progress.md](../../../templates/progress.md) on setup, and tick/update it after each phase. **Feed the brain** when a capture trigger fires (brain-method trigger table) — one-line confirm, keep moving.
6. Keep brain + bible + fingerprint + slop-floor loading **invisible** — the writer just writes; the guide enforces canon and voice behind the scenes.

Never dump the whole pipeline. Always end your turn with the single next step named.
