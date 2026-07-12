# Brain Method — the Cowriter memory

> Portable. One small, hard-capped file (`brain.md`, workspace root) that learns the writer and runs the workflow lean. Every skill loads it **first** — it's cheap — and it decides what *else* is worth loading. The brains of the operation.

> Core principle: **a fact earns its line.** The brain is not a log. It's the distilled residue of working with this writer — small enough to load every single turn for near-zero tokens.

---

## What the brain is for (three jobs)

1. **Learn the writer.** Standing rules ("never em-dashes"), lasting steers ("always less purple"), defaults (creativity dial 1.2). Things true across projects and contexts, not per-project canon.
2. **Learn the workflow.** Observed habits: phases they skip, revision passes they actually run, how they like output presented, session rhythm.
3. **Cut tokens.** Load directives that tell skills what to *skip*: stable artifacts not worth re-deriving, files not worth re-reading, context-stack items this writer never needs.

## What it is NOT

- **Not the bible.** Story canon lives in `projects/<book>/bible/`. Never mirror it here.
- **Not progress.md.** Per-book roadmap state stays per-book.
- **Not a style-guide.** Per-book voice lives in `style/`. The brain holds only *writer-level* prose defaults that apply to every book unless a book's fingerprint/style-guide overrides them.
- **Not a transcript.** No one-off feedback, no session notes, no history.

---

## The file: `brain.md`

Lives at the workspace root. **Hard cap: 100 lines / ~800 words.** One fact per line, imperative form, terse. Structure:

```markdown
# Brain
<!-- cap: 100 lines. A fact earns its line. Distill or evict before adding. -->

## Writer — standing rules
- No em-dashes, ever. (explicit, 2026-07)
- Creativity dial default 1.2.

## Steers that stuck
- Less purple atmosphere; cut on sight. (steered 3x)

## Workflow
- Skips read-aloud pass; don't offer it.
- Wants scene shown whole, then one question — no mid-scene check-ins.

## Efficiency — load directives
- <book>: fingerprint locked; never reload style/samples/.
- Bible loads: canon-facts + only characters IN the scene.
```

Line format: `- <fact in imperative form>. (<provenance: explicit | steered Nx | observed Nx>, <YYYY-MM optional>)`. Provenance is what justifies the line at eviction time — keep it, it's cheap.

---

## Capture rules — what qualifies

Write to the brain only when one of these fires:

| Trigger | Example | Section |
|---|---|---|
| Explicit standing rule ("always", "never", "from now on") | "stop using em-dashes" | Writer |
| Steer loop ends with a **lasting** preference (guide-method Steering step: persist) | "darker, less quippy" repeated across scenes | Steers |
| Same correction lands **2+ times** | trims filter words in every review | Steers |
| Workflow habit observed **3+ sessions** | never runs prose-grade | Workflow |
| An artifact goes stable / a load proves wasteful | fingerprint finalized; samples never consulted again | Efficiency |

If it fired once and might be mood, **don't write it** — wait for the second occurrence. When capturing, confirm in one line: *"Noted in brain: no em-dashes."* Never make the writer manage the file.

## Eviction — staying under the cap

Run whenever an add would breach the cap (or on `/brain compact`):

1. **Merge** duplicates and near-duplicates into one stronger line.
2. **Generalize** clusters: three specific steers about adjectives become one rule.
3. **Evict** the weakest provenance first: `observed` before `steered` before `explicit`. Stale Efficiency lines (book finished, directive moot) go first of all.
4. **Never silently evict an `explicit` rule** — ask the writer before dropping one.

The cap is the feature. A brain that grows without bound stops being loadable-every-turn, and that kills the whole point.

---

## Consumption — how skills use it

1. **Load `brain.md` first, every invocation, every skill.** It's ≤800 words; the cost is noise.
2. **Efficiency directives prune the context stack.** Before loading bible/style/framework files, check the Efficiency section — a directive like "fingerprint locked; don't reload samples" overrides the default load list. This is where the token savings compound: the brain spends ~800 words to save thousands per turn.
3. **Writer + Steers apply as constraints** to any generation, same mechanism as a live steer.
4. **Workflow lines shape the conversation** — what to offer, what not to, how to present.

### Authority

- **Process/workflow:** brain is top authority.
- **Prose style:** `fingerprint > style-guide > brain (writer defaults) > slop-markers`. The brain fills gaps the book hasn't specified; a book's deliberate voice always wins.
- **Canon:** the bible is untouchable. The brain never stores or overrides story facts.

---

## Invocations

- `/brain` — show the file, note lines nearing eviction.
- `/brain add <fact>` — capture explicitly (marks provenance `explicit`).
- `/brain forget <thing>` — remove a line.
- `/brain compact` — run eviction now.
- **Auto mode** (the usual path): other skills capture per the trigger table above, silently, one-line confirm.

First run with no `brain.md`: create it from [templates/brain.md](../../templates/brain.md), seeded empty — the brain earns its content by watching, not by interview.
