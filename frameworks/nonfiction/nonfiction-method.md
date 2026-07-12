# Non-fiction Method — brief, facts, outline, sections

> Portable. One method for every persistent non-fiction project: articles, essays, guides, blog posts, marketing copy, reports, proposals. They differ by the `form:` field in `brief.md`, not by separate pipelines. This is the bible's lightweight cousin — same discipline, a fraction of the scaffolding.

## Project shape

```
projects/<name>/
  brief.md      # thesis/message, audience, goal, form, tone, length target, "what this is NOT"
  facts.md      # numbered claims + source + status — the continuity layer (skippable for opinion/voice pieces)
  outline.md    # sections: one-line job + claim IDs used + word budget
  drafts/       # one file per section or per version
  style/        # same shape as fiction: style-guide.md, optional style-fingerprint.md + samples/
  progress.md
```

Marker: `brief.md` at project root = non-fiction project. (`bible/` = fiction.)

## Phases (mirrors the fiction pipeline)

| # | Phase | What happens | Method |
|---|-------|--------------|--------|
| 0 | **Setup** | Create project from `templates/nonfiction/` | this file |
| 1 | **Brief** | Thesis, audience, goal, form, tone, length | this file, below |
| 2 | **Facts** *(skippable)* | Gather claims + sources | this file, below |
| 3 | **Voice** | Fingerprint from samples, or style-guide knobs | [style-fingerprint-schema.md](../craft/style-fingerprint-schema.md) → style-learn |
| 4 | **Outline** | Argument structure with section budgets | this file, below |
| 5 | **Draft** | Write sections | this file, below |
| 6 | **Fact-fold** | Update `facts.md` from claims made while drafting | this file, below |
| 7 | **Revise** | critique (argument lens) → pacing → voice → line-edit → slop-check → prose-grade → read-aloud | [revision-methods.md](../revision/revision-methods.md) |

State detection, same rule as fiction: earliest unmet phase is the *suggested* next step; the writer can jump anywhere. `brief.md` still placeholders → Phase 1; `facts.md` empty and the piece needs evidence → offer Phase 2; no fingerprint → offer Phase 3 (a style-guide alone is fine for most non-fiction); `outline.md` stub → Phase 4; `drafts/` empty → Phase 5.

## Phase 1 — Brief

Conversational, one question per turn. Capture in `brief.md`:

- **Thesis / message** — the one sentence the reader should walk away with. No thesis, no piece.
- **Audience** — who reads it, what they already know, what they're skeptical of.
- **Goal** — inform / persuade / convert / instruct. This sets structure defaults.
- **Form** — `article | essay | guide | blog | marketing | report | proposal`. Sets register + length defaults ([length-method.md](../craft/length-method.md), non-fiction cascade).
- **Tone** — two or three adjectives, plus any register constraint ("no jargon", "first person ok").
- **Length target** — one integer, from the form default unless the writer names one.
- **What this is NOT** — the scope fence; kills bloat before it starts.

## Phase 2 — Facts (the continuity layer)

For anything making checkable claims. Each entry in `facts.md`:

```
F3. Remote workers report 22% higher satisfaction — [Gallup 2025 survey](url) — verified
```

Numbered ID, claim, source, status (`verified | asserted | needs-check`). Rules:

- Drafting may only assert what's in `facts.md` or what's common knowledge; anything else gets written in and marked `needs-check` — never silently invented. **This is the non-fiction slop line: no fabricated statistics, quotes, or citations, ever.**
- Skippable for pure-opinion and voice pieces; say so and move on.

## Phase 4 — Outline (argument structure)

Structure by goal: persuade → problem/stakes/solution/objections/call; inform → inverted pyramid or chronological; instruct → prerequisites/steps/pitfalls; convert → hook/pain/promise/proof/ask. Offer the default for the form; let the writer swap.

Each section gets one line in `outline.md`:

```
S2. The hidden cost — make the reader feel the problem — uses F1, F3 — ~300 words
```

Job + claim IDs + budget. Budgets cascade from the brief's length target (length-method, non-fiction cascade). Every section must move the thesis forward; a section with no job is a cut.

## Phase 5 — Draft sections

Load the context stack per [context-map.md](../core/context-map.md) (non-fiction column: brief + facts + outline + voice + slop floor). The section unit replaces fiction's goal/conflict/turn:

- **Claim** — the section's one point (from its outline job).
- **Evidence** — the facts/examples that earn it (cite `facts.md` IDs).
- **So-what** — why the reader should care; tie back to thesis.
- **Handoff** — a reason to keep reading; end on motion, not summary.

Drafting rules: lead with the point (no throat-clearing windups); concrete examples over abstraction; one idea per paragraph; obey slop-markers minus the project's exceptions; write to the section budget as a soft target. Headings, lists, and pull-quotes are voice decisions — follow the fingerprint/style-guide, and the form's conventions (a report tolerates structure a personal essay doesn't).

After drafting: self-check against slop-markers; list any **new claims** asserted while drafting under the draft:

```
--- new claims to log (fold into facts.md) ---
- 
```

## Phase 6 — Fact-fold

The bible-update equivalent, done inline by the guide: fold the draft's new-claims block into `facts.md` (new IDs, `needs-check` until sourced), flag any draft claim that *contradicts* an existing fact instead of overwriting either. Report the changelog in two lines.

## Phase 7 — Revise

Same passes as fiction via [revision-methods.md](../revision/revision-methods.md), with critique using its **non-fiction lens**: argument logic, evidence sufficiency (does every claim have a leg?), audience fit, structure, thesis clarity. `continuity`'s job is covered by checking drafts against `facts.md`. slop-check / line-edit / prose-grade / read-aloud run unmodified.
