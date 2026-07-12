---
name: brain
description: The Cowriter memory — a hard-capped brain.md that learns the writer's standing rules, lasting steers, and workflow habits, and issues load directives that cut token cost for every other skill. Use to view, add, forget, or compact what Cowriter knows about how you write. Other skills read it first and write to it automatically.
---

# brain

Maintain the writer's brain per [brain-method.md](../../../frameworks/guide/brain-method.md).

1. If `brain.md` is missing at the workspace root, create it from [templates/brain.md](../../../templates/brain.md).
2. Route the ask:
   - no args → show the file; flag lines nearing eviction and any stale Efficiency directives.
   - `add <fact>` → distill to one line, provenance `explicit`, append to the right section.
   - `forget <thing>` → remove the matching line (confirm if it's an `explicit` rule).
   - `compact` → run the eviction pass: merge → generalize → evict weakest provenance; never drop `explicit` without asking.
3. **Enforce the cap** (100 lines / ~800 words) on every write — compact before adding, never after.
4. Capture rules for auto mode (invoked from other skills): only facts that pass the trigger table in the method — explicit standing rules, lasting steers, 2+ repeated corrections, 3+ session habits, stable-artifact notices. One-line confirm, then back to the writing.

Authority: process → brain wins; prose → `fingerprint > style-guide > brain > slop-markers`; canon → bible only, never the brain.
