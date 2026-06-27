# Outline Method

> Portable. Build a beat sheet for a long-form work. Pick a structure or let the writer choose. Output goes to `projects/<book>/outline.md`.

## Inputs
- `bible/premise.md` (logline, theme, conflict, **Length target**) — the outline must serve these.
- `bible/characters.md` — arcs the plot must deliver.
- `style/style-fingerprint.md` → **scene-length** block (`avg_scene_words`), if voice is set — sets scene granularity.
- Chosen structure (ask if unset; default **3-act**).

## Structures on offer
- **3-act** — Setup / Confrontation / Resolution. Safe default.
- **Save the Cat** — 15 beats (Opening Image → Final Image). Good for tight commercial pacing.
- **Hero's Journey** — 12 stages. Myth/quest shapes.
- **Story circle (Dan Harmon)** — 8 steps. Character-driven, episodic-friendly.
- **Custom** — writer defines acts.

## Method
1. Confirm structure. State theme + protagonist's want/need/lie up front (from bible).
2. Generate beats for the chosen structure. Each beat:
   ```
   ### Beat <n> — <name>
   - Purpose: <what it does for plot AND arc>
   - What happens: <1–3 sentences>
   - Turn / value shift: <+/-, what changes>
   - Sets up: <thread> | Pays off: <thread>
   - POV / location: <...>
   - Budget: <words> | Tier: <micro|short|standard|extended>
   ```
3. **Cascade the length budget** (see [length-method.md](../craft/length-method.md)). Top-down from the premise's **Length target**:
   - Split the total across acts by the structure's proportions (3-act ≈ 25/50/25), weighted by dramatic load — not evenly.
   - Give each beat a share of its act, **uneven on purpose**: climax/midpoint beats denser, connective beats lean.
   - Set each beat's `Budget` (words) and `Tier`. Scene count for a beat ≈ `budget / avg_scene_words` (from the fingerprint; fall back to register default if voice unset, and confirm the avg with the writer). The whole-book scene count falls out of `target / avg_scene_words`.
   - Present the split; let the writer nudge any beat. Remaining beats reflow to hold the total.
4. Pressure-test against the bible:
   - Does every beat escalate? No flat middle.
   - Does the protagonist's internal arc move alongside the plot?
   - Is each setup paid off, each payoff set up? Cross-check `timeline.md` → Open threads.
5. Flag the weakest beat and why; offer alternatives.

## Output
Write `outline.md`: structure name, theme line, **the total length target + per-act split**, then the beat list (each with `Budget` + `Tier`). Keep it revisable — outline is a hypothesis, not a contract; budgets are a compass, not a cap.
