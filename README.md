# Cowriter

A co-writer for everything you write. A two-line email counts. So does a novel. One front door, `/cowrite`, figures out which you're doing and gets you drafting fast. You never have to learn 23 skill names.

## Three tracks, one front door

`/cowrite` reads your opening ask (or the marker files in an existing project) and routes to one of three tracks. You never pick a mode explicitly; if it's genuinely unclear, it asks you one question, not a menu.

| Track | For | What it creates |
|---|---|---|
| **Quick** | An email, a dispute letter, a reply, a short post | Nothing, by default. The draft happens in-chat after at most 2 questions. A recurring situation (an ongoing dispute, a work-email persona) can be saved as `contexts/<name>/` so the next reply remembers your position and tone. |
| **Non-fiction** | An article, essay, guide, blog post, marketing copy, report, or proposal | `projects/<name>/` holding `brief.md` (thesis, audience, goal), `facts.md` (claims + sources, so nothing gets fabricated), and `outline.md` (sections with word budgets). One shape for all seven forms; a `form:` field in the brief is the only thing that changes. |
| **Fiction** | A short story or novel | `projects/<book>/` with a living `bible/` (canon), `outline.md` (beats), and `drafts/`. The original pipeline, unchanged. |

Whichever track you're on, the same layer runs underneath: a quality floor that kills AI-writing tells, a style fingerprint learned from your own samples, and a memory (`brain.md`) that learns your standing rules and stops re-asking things you've already told it. That contract is defined once in [`frameworks/core/context-map.md`](frameworks/core/context-map.md); it's why adding two new tracks didn't mean building two new toolkits.

## Get started

```
/cowrite
```

That's the whole interface. Tell it what you're writing ("an email to my landlord," "an article about remote work," "I want to write a novel") and it takes it from there: one question at a time, output shown before the next one, with a steer loop the moment something feels off (say so, and it fixes the actual thing rather than a generic rewrite).

No idea yet for a book? Start a stage earlier:

```
/brainstorm
```

This diverges hard from the generic version of your idea, twists it off the statistical center, and hands a pressure-tested premise straight to `/cowrite`. Already have an idea? `/brainstorm <your idea>` starts from it.

Resuming later, on any track, is the same command: `/cowrite`. It reads the project's `progress.md` and picks up where you stopped.

## What's actually happening underneath

- **The craft layer** (`frameworks/craft/`) holds a slop kill-list ([`slop-markers.md`](frameworks/craft/slop-markers.md)) that catalogs the specific tells that make prose read like generic AI output, plus a style-fingerprint schema that turns your own writing samples into a measurable voice spec. Authority order when they'd conflict: **style-fingerprint > style-guide > brain > slop-markers**. Your deliberate voice always beats the generic floor.
- **The brain** (`brain.md`, [`brain-method.md`](frameworks/guide/brain-method.md)) is a single file, hard-capped at 100 lines, that every skill loads first. It remembers standing rules ("never use em-dashes"), steers that stuck, and workflow habits, and issues load directives that prune what else gets pulled into context. That's the mechanism keeping this from getting slow as projects pile up.
- **The bible** (fiction only, `frameworks/bible/`) is a living canon file per book, so a detail set in chapter 2 doesn't quietly drift by chapter 12.
- **Facts** (non-fiction's version of the bible, `facts.md`) are numbered claims with sources and a status (verified / asserted / needs-check). Drafting can only assert what's in here or common knowledge; nothing gets invented and passed off as sourced.

Everything above is portable markdown rather than code. Every file in `frameworks/` is written to be pasted directly into any AI chat (Claude.ai, ChatGPT, whatever) as a rules block, with or without Cowriter's own skill wrappers. The `.claude/skills/*/SKILL.md` files are thin; they point at the framework files instead of duplicating them.

## Layout

```
Cowriter/
├── README.md
├── brain.md              # writer-level memory, hard-capped, shared across everything below
├── .claude/skills/        # 23 Claude Code entry points (thin wrappers over frameworks/)
├── frameworks/            # the real method content: portable, paste-into-any-chat markdown
│   ├── core/               # context-map.md: what each track loads, defined once
│   ├── guide/               # cowrite conductor, brain, quick-track methods
│   ├── nonfiction/          # brief/facts/outline/section-drafting method
│   ├── bible/, prewriting/, drafting/, revision/   # fiction pipeline
│   └── craft/               # slop-markers, style-fingerprint schema, length budgets
├── brainstorm/             # fiction's ideation stage (the former standalone Brainstormer)
├── templates/              # blank scaffolds copied per project
│   ├── bible/, style/, progress.md, brain.md      # fiction
│   ├── nonfiction/                                 # brief.md, facts.md, outline.md, progress.md
│   └── context/                                    # quick-track saved-context scaffold
├── projects/               # your actual books and non-fiction projects live here
│   └── <name>/  (bible/ + outline.md + drafts/   or   brief.md + facts.md + outline.md + drafts/)
├── contexts/               # saved quick-track situations (an ongoing dispute, a persona)
│   └── <name>/  (brief.md + log.md + optional style/)
└── examples/test-book/     # worked fixture, kept out of projects/ so /cowrite greets new writers
```

## Or drive skills directly (advanced)

`/cowrite` is the recommended path: it sequences everything below in the right order and keeps context loading invisible. If you want a specific pass without the guide:

**Fiction:** `/bible-init` scaffolds a project → drop samples in `style/samples/` and run `/style-learn` → `/premise`, `/character`, `/world`, `/outline` → `/scene` to draft → `/slop-check`, `/continuity`, `/critique` to revise → `/bible-update` folds new canon back in.

**Non-fiction:** same shape, lighter: brief and facts instead of bible, `/expand` or `/continue` to draft sections, the same revision skills after.

**Any mode:** `/line-edit`, `/slop-check`, `/prose-grade`, `/read-aloud` are fully generic; they work on any draft, project or not.

## Build status

All 23 skills are built across all three tracks:

- [x] Fiction pipeline: bible spine, prewriting, drafting, revision (the original build)
- [x] Craft floor: slop-markers, style-fingerprint schema, length budgets
- [x] Brain: writer-level memory shared across every project and context
- [x] Non-fiction track: brief/facts/outline project shape, one method for all seven forms
- [x] Quick track: zero-setup drafting, saved contexts for recurring situations

`examples/test-book/` is a worked fixture and is deliberately excluded from `/cowrite`'s project detection.