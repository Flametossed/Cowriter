# Cowriter

A workspace for AI-assisted creative writing of **long-form fiction** — from the first spark of an idea through a revised draft. It exists to fix the three things AI writing fails at:

1. **Originality of concept** — an upstream *ideation stage* ([brainstorm/](brainstorm/)) that diverges hard, then twists the idea off the statistical center, so the book doesn't start from a generic premise.
2. **Consistency** — a living *story bible* every skill reads from and writes back to, so canon never drifts.
3. **Quality** — a *craft layer* (a slop kill-list + a sample-driven style fingerprint) so prose doesn't read like generic AI output.

The ideation stage was formerly the separate **Brainstormer** tool; it now lives inside this workspace as [brainstorm/](brainstorm/), wired so `/brainstorm` hands a locked premise straight to `/cowrite`.

## How it's meant to be used

Everything here is **dual-use**:

- **As Claude Code skills** — invoke `/bible-init`, `/scene`, `/slop-check`, etc. in this workspace. Entry points live in `.claude/skills/`.
- **As a portable prompt library** — the real method content lives in `frameworks/` as plain Markdown. Paste any of it into any AI chat (Claude.ai, ChatGPT, etc.) as a rules/context block. The `.claude/skills/*/SKILL.md` files are thin wrappers that point at these frameworks — no duplicated content.

## Layout

```
Cowriter/
├── README.md
├── .claude/skills/          # Claude Code entry points (thin wrappers)
├── brainstorm/              # IDEATION stage (the former Brainstormer)
│   ├── frameworks/          #   spark, twist, plot, beat, originality methods
│   ├── templates/           #   session-log scaffold
│   └── sessions/            #   your brainstorm logs live here
├── frameworks/              # PORTABLE method content (the real meat)
│   ├── bible/               # how to build/update/query canon
│   ├── craft/               # slop-markers + style fingerprint method
│   ├── prewriting/          # premise, character, world, outline methods
│   ├── drafting/            # scene, expand, continue, dialogue methods
│   └── revision/            # continuity, critique, line-edit, pacing methods
├── templates/               # blank scaffolds to copy per project
│   ├── bible/
│   └── style/
└── projects/                # your actual novels live here
    └── <book-name>/
        ├── bible/           # this book's living canon
        ├── style/           # samples + fingerprint + style guide
        ├── outline.md
        └── drafts/
```

## The three sources of authority

When skills make decisions, they resolve conflicts in this order:

```
style-fingerprint (learned from your samples)
   > style-guide (your manual knobs)
      > slop-markers (generic quality floor)
```

This keeps the quality layer from sanding off intentional voice. If your style deliberately uses fragments or heavy em-dashes, the fingerprint wins over the generic slop rule.

## Start here: `/cowrite`

**The front door.** You don't need to learn the skill names. Run:

```
/cowrite
```

It detects where your project is, then walks you through it one step at a time — premise → characters → voice → outline → drafting → revision — routing to the right tool automatically and keeping your story bible and voice consistent behind the scenes. Run it again anytime to pick up where you left off; each book's `progress.md` is the live roadmap.

**No idea yet?** Start one stage earlier:

```
/brainstorm
```

It invents an original concept — many sparks, then twist off the generic default, then a pressure-tested premise + subverted beat sketch — and writes the result straight into `projects/<book>/`. From there `/cowrite` resumes at the outline. (Already have an idea? `/brainstorm <your idea>` starts from it; or skip straight to `/cowrite`.)

## Or drive the skills directly (advanced)

1. `/bible-init <book-name>` — scaffolds `projects/<book-name>/` from templates.
2. Drop writing samples into `projects/<book-name>/style/samples/`.
3. `/style-learn <book-name>` — builds the style fingerprint.
4. `/premise`, `/character`, `/world`, `/outline` — pre-writing.
5. `/scene` — draft (style + bible aware).
6. `/slop-check`, `/continuity`, `/critique` — revise.
7. `/bible-update` — fold new canon from the draft back into the bible.

## Build status

- [x] Plan
- [x] Bible spine (templates + init/update/check)
- [x] Craft floor (slop-markers + style-guide template)
- [x] Sample-driven voice (style-learn)
- [x] Vertical slice (outline → scene → slop-check → continuity)
- [x] Remaining skills (premise, character, world, expand, continue, dialogue, critique, line-edit, pacing, voice, prose-grade, read-aloud)

All 21 skills built. `examples/test-book/` is a worked smoke-test example (kept out of `projects/` so `/cowrite` greets new writers instead of resuming the fixture).

## Full skill list

| Phase | Skills |
|-------|--------|
| **Ideation (upstream)** | **`brainstorm`** — invent an original concept, then hand off to `/cowrite` (toolkit in [brainstorm/](brainstorm/)) |
| **Guide (start here)** | **`cowrite`** — conducts all of the below |
| Bible / memory | `bible-init` · `bible-update` · `bible-check` |
| Craft / quality | `style-learn` · `slop-check` |
| Pre-writing | `premise` · `character` · `world` · `outline` |
| Drafting | `scene` · `expand` · `continue` · `dialogue` |
| Revision | `critique` · `pacing` · `voice` · `line-edit` · `prose-grade` · `read-aloud` · `continuity` |

Suggested revision order: `critique → pacing → voice → line-edit → slop-check → continuity → prose-grade → read-aloud`.
