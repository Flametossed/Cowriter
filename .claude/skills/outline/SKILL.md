---
name: outline
description: Build a beat sheet for a long-form work using a chosen structure (3-act, Save the Cat, Hero's Journey, Story Circle, or custom), driven by the book's premise and character arcs. Writes projects/<book>/outline.md.
---

# outline

Generate the plot outline.

1. Load `bible/premise.md` (incl. **Length target**), `bible/characters.md`, and the fingerprint's **scene-length** if voice is set.
2. Confirm structure with the user (default **3-act** if unset).
3. Follow [outline-method.md](../../../frameworks/prewriting/outline-method.md): generate beats, **cascade the length budget** (total → acts → beats, uneven; set each beat's `Budget`+`Tier` per [length-method.md](../../../frameworks/craft/length-method.md)), then pressure-test escalation, arc movement, and setup/payoff against the bible.
4. Write `projects/<book>/outline.md` with the per-act split + per-beat budgets.

Flag the weakest beat and offer alternatives. Outline is revisable, not a contract.
