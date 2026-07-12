# Quick Method — zero-setup writing

> Portable. For one-off pieces with a real recipient or immediate use: emails, dispute letters, cover letters, replies, announcements, short posts. No project, no phases, no files — ask almost nothing, draft, steer. The whole point is speed; every unnecessary question is a bug.

## Flow

1. **Brain first** — `brain.md` ([brain-method.md](brain-method.md)). Standing rules and steers apply to quick tasks automatically; no em-dash rules and tone defaults live here.
2. **Check for a saved context** — if `contexts/<name>/` matches the situation (same recipient, same dispute, same persona), load its `brief.md` + `log.md` and skip questions it already answers. Say so in one line ("Using your landlord context").
3. **Gather the brief in ≤2 questions.** Most asks already contain the audience ("email to my landlord") — don't re-ask what's given. Fill the gaps only:
   - **Goal** — what should the recipient do/feel after reading?
   - **Tone** — if not inferable from the situation (formal complaint vs note to a friend). Offer 2–3 options rather than an open question.
   Anything else (key facts, constraints, the thread being replied to) the writer usually pastes; take it, don't interrogate.
4. **Draft immediately.** Context stack per [context-map.md](../core/context-map.md), quick column: in-chat brief (+ saved context), voice from saved `style/` or brain defaults, [slop-markers.md](../craft/slop-markers.md) floor. Register-match the form — a dispute letter is firm and documented, a thank-you is warm and short. Length: as short as the job allows.
5. **Show + steer.** Present the draft, ask one forward question. Any dislike runs the standard steer loop (guide-method): pin cause → constraint → regenerate. Polishing passes (slop-check, line-edit, read-aloud, prose-grade) are available on request — don't run them unsolicited on a three-line email.
6. **Feed brain** on capture triggers as usual (a tone correction that lands twice is a standing rule).

## Quick drafting rules

- Lead with the point; the reader should know why they got this by line two.
- One ask per message. Bury nothing.
- Concrete specifics (dates, amounts, prior contacts) over vague grievance — especially in disputes.
- Match the power dynamic: firm ≠ rude, warm ≠ sloppy. Escalation letters state facts, cite prior contact, name the requested remedy and a deadline.
- Obey slop-markers; brain's writer rules are the standing voice.

## Saved contexts — continuity without a project

For recurring situations: an ongoing dispute, a work-email persona, a newsletter voice.

**When to offer (once, don't nag):** the second piece for the same recipient/situation, or a multi-round exchange is clearly underway. *"Want me to save this as a standing context so follow-ups keep the same position and tone?"*

**Shape** — `contexts/<name>/`, scaffolded from [templates/context/brief.md](../../templates/context/brief.md):

```
contexts/<name>/
  brief.md    # situation, audience, my position, tone, do/don't
  log.md      # one line per piece sent: date — gist — outcome if known
  style/      # optional: persona fingerprint/samples (style-learn works here)
```

**Rules:** append one line to `log.md` after each piece the writer accepts; never contradict a position taken in the log (that's the quick track's continuity check); a context is a standing situation, not a work-in-progress — it has no phases and no progress.md.

## Escalation — when a quick task outgrows itself

If the piece keeps growing (structure appears, >~1,000 words, "actually this is becoming an article"), offer **once** to promote it to a non-fiction project ([nonfiction-method.md](../nonfiction/nonfiction-method.md)): create `projects/<slug>/` from templates, carry the drafted text into `drafts/` and the gathered answers into `brief.md`. If declined, keep going inline without re-offering.
