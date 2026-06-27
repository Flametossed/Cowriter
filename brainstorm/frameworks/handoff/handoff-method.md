# Handoff Method — into the book project

> Portable (within this workspace). Package the locked concept — premise, plot engine, beat sketch — into Cowriter's bible format and write it into `projects/<book>/`, so the writer can run `/cowrite` and continue straight into characters, voice, and drafting.

> Brainstorm **ends** exactly where Cowriter's `/premise` and `/outline` would otherwise start from a blank seed. The writer arrives at the drafting stage not with a vibe, but with a pressure-tested, original spine already on disk — in the same workspace, no repo switch.

---

## Preconditions

Don't hand off a soft concept. Confirm before writing:
- Premise is locked and **passed the originality battery** (`originality-tests` — especially seen-it, specificity, engine).
- Plot engine exists (irreversible first move + escalation logic).
- A beat sketch exists (turns with default-vs-chosen moves). *Optional but recommended — Cowriter can outline from premise alone, but the subverted turns are the point.*

If any are soft, say so and route back — handoff is not the place to paper over a weak spine.

---

## Step 1 — Name the book & scaffold

1. Get a display title (or working title) and **kebab-case** it for the folder: *The Debt City* → `the-debt-city`.
2. Check `projects/<book>/`:
   - **Missing** → scaffold it from Cowriter's templates ([templates/bible/](../../../templates/bible/) and [templates/style/style-guide.md](../../../templates/style/style-guide.md)), replacing every `{{BOOK_TITLE}}` with the display title, and create `progress.md` from [templates/progress.md](../../../templates/progress.md). This is exactly what Cowriter's `bible-init` does — mirror it so the project is well-formed.
   - **Exists** → don't clobber. If `premise.md` already has real content, show it and ask: overwrite, merge, or pick a new name.

---

## Step 2 — Map the concept into `bible/premise.md`

Fill Cowriter's premise template ([templates/bible/premise.md](../../../templates/bible/premise.md)) from the session log. Field by field:

| Cowriter field | Source in the brainstorm log |
|----------------|--------------------------------|
| **Logline** | The locked logline (`[protagonist] must [goal] or [stakes], but [obstacle]`). |
| **Premise (2–4 sentences)** | The twisted concept + the plot engine's squeeze, in prose. |
| **Theme — Central question** | Derive from the philosophical conflict the twist exposed; phrase as a *question*, never a moral. |
| **Central conflict — External** | The plot engine's irreversible move + escalation. |
| **Central conflict — Internal** | The protagonist's flaw the engine forces open (the Lie, in Cowriter terms). |
| **Central conflict — Philosophical** | value vs. counter-value the premise stages. |
| **Genre / tone — Comps** | The comps named in the seen-it test ("X meets Y"). |
| **Tone** | From the session log's tone notes / persisted steers. |
| **Promise to the reader** | The *anchor* from the familiarity dial — the familiar experience the book delivers. |
| **What this book is NOT** | The **defaults you deliberately rejected** in `twist-method`. This is the highest-value handoff: the named-and-avoided tropes become Cowriter's guardrails, so drafting never drifts back to the center. |

> The "what this is NOT" list is the bridge that makes the whole framework pay off. Every default the brainstorm stage named and refused goes here as an explicit guardrail Cowriter's skills will respect downstream.

---

## Step 3 — Map the beat sketch into `outline.md`

Write a starter `outline.md` in Cowriter's shape ([example](../../../examples/test-book/outline.md)):
- Header: `Structure: <chosen or "TBD — Cowriter to choose">` and a one-line theme.
- One block per turn from the beat sketch:
  ```
  ### Turn <n> — <structural job>
  - What happens: <chosen move>
  - Avoided default: <the cliché we rejected>
  - Pays off / sets up: <threads>
  ```
- Close with a note: *"Beat sketch from the brainstorm stage — turns are deliberately subverted. Cowriter's `/outline` should choose the structure and expand each into full beats with value-shifts and POV."*

Leave structure selection to Cowriter unless the writer already chose one — that's `outline-method`'s job, with the full character bible in hand.

---

## Step 4 — Report & redirect

After writing, report concisely:
- The tree created/updated under `projects/<book>/`.
- Which premise fields were filled vs. left for Cowriter.
- The guardrails written into "What this is NOT".

Then name the next step plainly: *"Run `/cowrite` (or `/character`) to build your protagonist and voice. The premise and a subverted beat sketch are already waiting in `projects/<book>/`."* Same workspace — no repo to switch to.

Mark **Handoff = done** in the session log. The ideation stage is complete; Cowriter owns everything downstream.
