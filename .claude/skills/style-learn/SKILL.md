---
name: style-learn
description: Read the writing samples in a book's style/samples/ folder and produce a measurable style-fingerprint.md — sentence metrics, voice, signature moves, diction, and a paste-ready style prompt. Use after adding samples, or to capture a target author's technique.
---

# style-learn

Turn samples into a style fingerprint.

1. Locate `projects/<book>/style/samples/` (book from args).
2. Follow [style-fingerprint-schema.md](../../../frameworks/craft/style-fingerprint-schema.md) exactly.
3. Measure with numbers + representative quotes; separate **signature** from **avoids**.
4. For `emulate-comp` samples: capture technique only, never reproduce text.
5. **Derive the scene-length block** (`avg_scene_words` + `tendency`) — measured from full scenes if present, else inferred from prose density. Feeds the length budget (`length-method.md`).
6. Write the result to `projects/<book>/style/style-fingerprint.md` using the schema.
7. Fill the **slop-marker reconciliation** section so `slop-check` knows which generic rules this voice intentionally breaks.

Report the headline traits and the paste-ready style prompt. Remind: fingerprint is regenerated, not hand-edited — manual tweaks go in `style-guide.md`.
