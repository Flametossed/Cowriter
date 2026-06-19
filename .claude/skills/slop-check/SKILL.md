---
name: slop-check
description: Scan a draft for AI-writing tells (antithesis tics, filter words, named emotions, purple atmosphere, dead clichés, default diction) and report flags with fixes plus a density score. Respects the book's intentional style exceptions. Use to quality-check prose.
---

# slop-check

Hunt slop in a draft.

1. Load the draft (from args or latest in `drafts/`).
2. Load the authority stack: `style/style-fingerprint.md` and `style/style-guide.md` (their **allowed exceptions** + reconciliation), then [slop-markers.md](../../../frameworks/craft/slop-markers.md).
3. Scan against every marker category. **Do not flag** anything the fingerprint/style-guide marks intentional — `fingerprint > style-guide > slop-markers`.
4. Report per the format in slop-markers.md: `[category] "text" (file:line) — why / fix`, then a **density score** (markers per 1000 words) and the top 3 recurring offenders.

Flag + suggest; don't rewrite the whole passage unless asked. Keep the writer in control of the voice.
