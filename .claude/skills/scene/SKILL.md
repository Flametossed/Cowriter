---
name: scene
description: Draft a single scene from an outline beat, constrained by the story bible (canon) and the craft layer (style fingerprint + slop-markers). Writes to projects/<book>/drafts/. The core drafting skill.
---

# scene

Draft a bible-aware, voice-aware scene.

1. Get the beat (from `outline.md` or the user's ask).
2. Load the context stack per [scene-method.md](../../../frameworks/drafting/scene-method.md):
   - bible: [canon-facts + relevant character/world entries]
   - voice: `style/style-fingerprint.md` → `style/style-guide.md`
   - quality floor: [slop-markers.md](../../../frameworks/craft/slop-markers.md) minus this book's allowed exceptions
   - length: the beat's `Tier`+`Budget` from `outline.md` — write to the tier as a soft target ([length-method.md](../../../frameworks/craft/length-method.md))
3. Build the scene scaffold (goal/conflict/turn/hook) before prose.
4. Draft. Obey the quality contract; self-check against slop-markers before presenting.
5. Log actual words vs budget in `progress.md` → Length; surface the reflow choice on material drift.
6. Append the `new facts to log` block so `/bible-update` can capture improvised canon.

Authority on conflict: `fingerprint > style-guide > slop-markers`; canon is never overridden by style.
