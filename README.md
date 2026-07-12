[![standard-readme compliant](https://img.shields.io/badge/readme%20style-standard-brightgreen.svg?style=flat-square)](https://github.com/RichardLitt/standard-readme)
[![portable: any LLM](https://img.shields.io/badge/portable-any%20LLM-orange.svg?style=flat-square)](#run-in-any-llm)
[![license: MIT](https://img.shields.io/badge/license-MIT-green.svg?style=flat-square)](LICENSE)

# Cowriter

A co-writer for everything you write. A two-line email counts. So does a novel. One front door, `/cowrite`, figures out which you are doing and gets you drafting fast. You never have to learn 23 skill names.

Cowriter is a portable writing toolkit built as plain markdown. The real method lives in `frameworks/` and is written to be pasted straight into any AI chat. The `.claude/skills/` wrappers are thin convenience layers over those same files, so the method never gets duplicated and never drifts.

**It is not tied to Claude.** The `/cowrite` slash commands assume Claude Code, but the method underneath works anywhere you can paste markdown: ChatGPT, Gemini, Claude.ai, local LLM frontends, anything. See [Run in any LLM](#run-in-any-llm) for the no-install path.

## Table of Contents

- [Background](#background)
- [Install](#install)
- [Usage](#usage)
- [Run in any LLM](#run-in-any-llm)
- [How it works](#how-it-works)
- [Layout](#layout)
- [Advanced usage](#advanced-usage)
- [Project status](#project-status)
- [Maintainers](#maintainers)
- [Contributing](#contributing)
- [License](#license)

## Background

Writing tools tend to fall into one of two shapes. Either they are a single generic prompt that flattens your voice, or they are a sprawling app with a setting for every paragraph. Cowriter goes a third way: a small set of opinionated methods that learn your voice from your own samples, keep a living canon for each project, and hold a quality floor that kills the tells that make prose read as generic AI output.

It started as a fiction pipeline (a living bible, an outline of beats, scene drafts, and revision passes). The same backbone now serves non-fiction and quick one-off writing too, because the underlying contract is defined once in [`frameworks/core/context-map.md`](frameworks/core/context-map.md): what to load, in what order, and which layer wins on a conflict. Adding new tracks did not mean building new toolkits.

## Install

Two paths. Pick the one that matches where you write.

### Claude Code (guided, slash commands)

If you use [Claude Code](https://docs.anthropic.com/en/docs/claude-code), the 23 skills auto-register from `.claude/skills/`:

```sh
$ git clone https://github.com/Flametossed/Cowriter.git
$ cd Cowriter
```

Open the folder in Claude Code. The skills register on their own. No build step, no dependencies, no npm install. Everything underneath is markdown.

### Any LLM (no install)

If you do not use Claude Code, skip the skills entirely. Paste the files in `frameworks/` into any AI chat as a rules block. They were written to be read on their own.

```sh
$ git clone https://github.com/Flametossed/Cowriter.git
```

Then open [`frameworks/guide/guide-method.md`](frameworks/guide/guide-method.md) and [`frameworks/core/context-map.md`](frameworks/core/context-map.md) in your editor, copy their contents, and drop them into any chat window. Full instructions in [Run in any LLM](#run-in-any-llm) below.

## Usage

```
/cowrite
```

That is the whole interface. Tell it what you are writing ("an email to my landlord," "an article about remote work," "I want to write a novel") and it takes it from there: one question at a time, output shown before the next one, with a steer loop the moment something feels off. Say so, and it fixes the actual thing rather than handing you a generic rewrite.

`/cowrite` reads your opening ask (or the marker files in an existing project) and routes to one of three tracks. You never pick a mode explicitly. If it is genuinely unclear, it asks you one question, not a menu.

| Track | For | What it creates |
|---|---|---|
| **Quick** | An email, a dispute letter, a reply, a short post | Nothing, by default. The draft happens in-chat after at most 2 questions. A recurring situation (an ongoing dispute, a work-email persona) can be saved as `contexts/<name>/` so the next reply remembers your position and tone. |
| **Non-fiction** | An article, essay, guide, blog post, marketing copy, report, or proposal | `projects/<name>/` holding `brief.md` (thesis, audience, goal), `facts.md` (claims plus sources, so nothing gets fabricated), and `outline.md` (sections with word budgets). One shape for all seven forms; a `form:` field in the brief is the only thing that changes. |
| **Fiction** | A short story or novel | `projects/<book>/` with a living `bible/` (canon), `outline.md` (beats), and `drafts/`. The original pipeline, unchanged. |

No idea yet for a book? Start a stage earlier:

```
/brainstorm
```

This diverges hard from the generic version of your idea, twists it off the statistical center, and hands a pressure-tested premise straight to `/cowrite`. Already have an idea? `/brainstorm <your idea>` starts from it.

Resuming later, on any track, is the same command. Run `/cowrite` again; it reads the project's `progress.md` and picks up where you stopped.

## Run in any LLM

Cowriter is a portable method written in markdown, so you can run the entire pipeline in any chat that accepts text. You lose only the auto-loading magic. In Claude Code the skill wrapper reads `brain.md`, detects the mode from marker files, and pulls the right framework section. In a plain chat, you do that driving yourself. The method is the same; the conductor seat just moves from the wrapper to you.

### What to paste

Drop these into your chat window (or a custom-instructions / system-prompt slot, if the model surfaces one) as a rules block, in roughly this order:

1. [`frameworks/core/context-map.md`](frameworks/core/context-map.md): the contract. What to load per mode, which layer wins on conflict.
2. [`frameworks/guide/guide-method.md`](frameworks/guide/guide-method.md): the conductor. Its phase table tells you (and the model) what comes next.
3. `brain.md` from the repo root: your standing rules and steers. Replace it with your own once you have them.
4. The method file for the track you are on:
   - Fiction: [`frameworks/bible/bible-method.md`](frameworks/bible/bible-method.md), [`frameworks/prewriting/prewriting-methods.md`](frameworks/prewriting/prewriting-methods.md), [`frameworks/craft/style-fingerprint-schema.md`](frameworks/craft/style-fingerprint-schema.md), [`frameworks/prewriting/outline-method.md`](frameworks/prewriting/outline-method.md), [`frameworks/drafting/scene-method.md`](frameworks/drafting/scene-method.md), [`frameworks/revision/revision-methods.md`](frameworks/revision/revision-methods.md).
   - Non-fiction: [`frameworks/nonfiction/nonfiction-method.md`](frameworks/nonfiction/nonfiction-method.md), plus the same craft and revision files.
   - Quick: [`frameworks/guide/quick-method.md`](frameworks/guide/quick-method.md).
5. The living files for your project: `brain.md`, the project's `bible/` (or `brief.md` + `facts.md`), `style/style-fingerprint.md`, `outline.md`. Paste the current state at the start of each session, or keep them in a note you edit live.

That list looks long, but you only paste the files for the phase you are running. A fiction draft session loads the bible, the fingerprint, and `scene-method.md`. A critique session loads `premise.md` and `revision-methods.md`. The context-map tells the model which slot each file fills.

### What changes vs. Claude Code

- **No slash commands.** You drive the sequence by hand. Open `guide-method.md`, read its phase table, and tell the model which phase you are in ("we are at Phase 5, drafting beat 4"). The model then runs that method inline.
- **No auto-loading.** When a phase says "load the fingerprint," you paste it. When brain.md picks up a new steer, you edit the file yourself instead of letting the wrapper persist it.
- **No skill auto-discovery.** The 23 `/skill` entry points do nothing outside Claude Code. Skip them. The framework files they point at are the real method.
- **Everything else is identical.** The slop kill-list, the style fingerprint, the authority order (`style-fingerprint > style-guide > brain > slop-markers`), the canon enforcement, the one-step-at-a-time conductor rules. These are all just markdown the model reads.

### Compatibility

The method is model-agnostic and uses no Claude-specific features. The framework files are plain markdown, so they paste cleanly into Claude.ai, ChatGPT, Google Gemini, or any local frontend that exposes a system-prompt slot (LM Studio, Ollama Web UI, and friends). No modifications are required. If a model has a small context window, paste only the files for the current phase rather than the whole stack.

## How it works

The same layers run under every track.

- **The craft layer** (`frameworks/craft/`) holds a slop kill-list in [`slop-markers.md`](frameworks/craft/slop-markers.md) that catalogs the tells making prose read like generic AI output, each with a detection and a fix. It also holds a style-fingerprint schema that turns your writing samples into a measurable voice spec. Authority order when they conflict: **style-fingerprint > style-guide > brain > slop-markers**. Your deliberate voice always beats the generic floor.
- **The brain** (`brain.md`, [`brain-method.md`](frameworks/guide/brain-method.md)) is a single file, hard-capped at 100 lines, that every skill loads first. It remembers standing rules ("no em-dashes"), steers that stuck, and workflow habits, and issues load directives that prune what else gets pulled into context. That mechanism keeps the toolkit from getting slow as projects pile up.
- **The bible** (fiction only, `frameworks/bible/`) is a living canon file per book, so a detail set in chapter 2 does not quietly drift by chapter 12.
- **Facts** (non-fiction's version of the bible, `facts.md`) are numbered claims with sources and a status (verified, asserted, needs-check). Drafting can only assert what is in here or what is common knowledge. Nothing gets invented and passed off as sourced.

Everything above is portable markdown rather than code. Every file in `frameworks/` is written to be pasted directly into any AI chat as a rules block, with or without Cowriter's own skill wrappers. The `.claude/skills/*/SKILL.md` files are thin; they point at the framework files instead of duplicating them. See [Run in any LLM](#run-in-any-llm) for the paste-and-go walkthrough.

## Layout

```
Cowriter/
├── README.md
├── brain.md              # writer-level memory, hard-capped, shared across everything below
├── .claude/skills/        # 23 Claude Code entry points (optional; thin wrappers over frameworks/)
├── frameworks/            # the real method content: portable, paste-into-any-chat markdown
│   ├── core/               # context-map.md: what each track loads, defined once
│   ├── guide/               # cowrite conductor, brain, quick-track methods
│   ├── nonfiction/          # brief/facts/outline/section-drafting method
│   ├── bible/, prewriting/, drafting/, revision/   # fiction pipeline
│   └── craft/               # slop-markers, style-fingerprint schema, length budgets
├── brainstorm/             # fiction's ideation stage
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

## Advanced usage

`/cowrite` is the recommended path. It sequences everything below in the right order and keeps context loading invisible. If you want a single pass without the guide, drive the skills directly.

**Fiction:** `/bible-init` scaffolds a project. Drop samples in `style/samples/` and run `/style-learn`. Then `/premise`, `/character`, `/world`, `/outline`. Draft with `/scene`. Revise with `/slop-check`, `/continuity`, `/critique`. Finally `/bible-update` folds new canon back in.

**Non-fiction:** same shape, lighter. Brief and facts instead of a bible. Draft sections with `/expand` or `/continue`. Run the same revision skills after.

**Any mode:** `/line-edit`, `/slop-check`, `/prose-grade`, and `/read-aloud` are fully generic. They work on any draft, project or not.

## Project status

All three tracks are built across all 23 skills.

- [x] Fiction pipeline: bible spine, prewriting, drafting, revision (the original build)
- [x] Craft floor: slop-markers, style-fingerprint schema, length budgets
- [x] Brain: writer-level memory shared across every project and context
- [x] Non-fiction track: brief/facts/outline project shape, one method for all seven forms
- [x] Quick track: zero-setup drafting, saved contexts for recurring situations

`examples/test-book/` is a worked fixture. It is deliberately excluded from `/cowrite`'s project detection so new writers get a clean greeting.

## Maintainers

[@Flametossed](https://github.com/Flametossed).

## Contributing

Feel free to dive in. [Open an issue](https://github.com/Flametossed/Cowriter/issues/new) or submit pull requests against the `main` branch.

When editing a framework file, keep it portable: write it so it reads on its own when pasted into a chat that has never heard of Cowriter. Do not duplicate method content in the `.claude/skills/*/SKILL.md` wrappers; point at the framework file instead.

## License

[MIT](LICENSE) (c) Flametossed