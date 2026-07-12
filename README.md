[![standard-readme compliant](https://img.shields.io/badge/readme%20style-standard-brightgreen.svg?style=flat-square)](https://github.com/RichardLitt/standard-readme)
[![portable: any LLM](https://img.shields.io/badge/portable-any%20LLM-orange.svg?style=flat-square)](#run-in-any-llm)
[![license: MIT](https://img.shields.io/badge/license-MIT-green.svg?style=flat-square)](LICENSE)

# Cowriter

A co-writer for everything you write. A two-line email counts. So does a novel. One front door, `/cowrite`, figures out what you're doing and gets you drafting fast. You never learn 23 skill names.

Cowriter is a portable writing toolkit built as plain markdown. The real method lives in `frameworks/` and is written to be pasted straight into any AI chat. `.claude/skills/` are thin convenience wrappers over those same files, so the method never gets duplicated and never drifts.

**It is not tied to Claude.** The `/cowrite` slash commands assume Claude Code, but the method underneath works anywhere you can paste markdown: ChatGPT, Gemini, Claude.ai, local LLM frontends, anything. See [Run in any LLM](#run-in-any-llm) for the no-install path.

## Table of Contents

- [Background](#background)
- [How it works](#how-it-works)
- [Install](#install)
- [Usage](#usage)
- [Advanced usage](#advanced-usage)
- [Layout](#layout)
- [Run in any LLM](#run-in-any-llm)
- [Project status](#project-status)
- [Maintainers](#maintainers)
- [Contributing](#contributing)
- [License](#license)

## Background

Writing tools tend to fall into one of two shapes. Either a single generic prompt flattens whatever you throw at it into the same voice, or you're stuck hand-assembling a different workflow for every kind of writing: a bible for fiction, a fact sheet for nonfiction, nothing at all for a quick email.

Cowriter picks a shape based on what you're actually writing, then runs the right pipeline for it: a **Quick** track for one-offs, a **Non-fiction** track for anything claims-and-sources, and a **Fiction** track for anything with a bible and canon. All three share the same craft floor (slop kill-list, style fingerprint, standing rules in `brain.md`), so voice and quality stay consistent no matter which track you're on.

For the full shape of that decision, see [`frameworks/core/context-map.md`](frameworks/core/context-map.md).

## How it works

The same layers run under every track.

- **The craft layer** (`frameworks/craft/`) holds the slop kill-list in [`slop-markers.md`](frameworks/craft/slop-markers.md) and the AI style-fingerprint spec. Authority order on conflict: **style-fingerprint > style-guide > brain > slop-markers**. Your deliberate voice always beats the generic floor.
- **The brain** (`brain.md`, [`brain-method.md`](frameworks/guide/brain-method.md)) is a single file, hard-capped at 100 lines, that every skill loads first. It remembers standing rules ("no em-dashes"), steers you got stuck on, workflow habits, and load directives, and prunes everything else out of context. This mechanism is what keeps the toolkit from getting slow as projects pile up.
- **The bible** (fiction only, `frameworks/bible/`) is a living canon file per book, so a detail set in chapter 2 does not quietly drift by chapter 12.
- **Facts** (non-fiction's version of the bible, `facts.md`) is a numbered list of claims, sources, and status (verified, asserted, needs-check). Drafting draws only on what's in here plus common knowledge. Nothing gets invented and passed off as sourced.

Everything above is portable markdown rather than code. Every file in `frameworks/` is written to be pasted directly into any AI chat as a rules block, with or without Cowriter's own skill wrappers. `.claude/skills/*/SKILL.md` files are thin; they point to the framework files instead of duplicating them. See [Run in any LLM](#run-in-any-llm) for the paste-and-go walkthrough.

## Install

### Claude Code (guided, slash commands)

If you use [Claude Code](https://docs.anthropic.com/en/docs/claude-code), 23 skills auto-register from `.claude/skills/`:

```sh
$ git clone https://github.com/Flametossed/Cowriter.git
$ cd Cowriter
```

Open the folder in Claude Code. Skills register on their own. No build step, no dependencies, no npm install. Everything underneath is markdown.

### Any LLM (no install)

If you don't use Claude Code, skip the skills entirely. Paste the files in `frameworks/` into any AI chat as a rules block. They're written to be read on their own. See [Run in any LLM](#run-in-any-llm) below for exactly what to paste and when.

## Usage

```
/cowrite
```

That's the whole interface. Tell it what you're writing ("an email to my landlord," "an article about remote work," "I want to write a novel") and it takes it from there: one question at a time, output shown before the next one, steer the loop the moment something feels off. Say so, and it fixes the actual thing rather than handing you a generic rewrite.

`/cowrite` reads your opening ask (or marker files in an existing project) and routes to one of three tracks. You never pick a mode explicitly. If it's genuinely unclear, it asks you one question, not a menu.

| Track | For | What it creates |
|---|---|---|
| **Quick** | An email, dispute letter, reply, short post | Nothing, by default. In-chat only. |
| **Non-fiction** | An article, essay, guide, or one of seven other forms | `brief.md`, `facts.md` (claims plus sources, nothing gets fabricated), `outline.md` (sections with word budgets). One shape covers all seven forms; the `form:` field in the brief is the only thing that changes. |
| **Fiction** | A short story or novel | `projects/<book>/` with a living `bible/` (canon), `outline.md` (beats), `drafts/`. The original pipeline, unchanged. |

No idea for a book yet? Start a stage earlier:

```
/brainstorm
```

This diverges hard from the generic version of an idea, twists it off the statistical center, and hands a pressure-tested premise straight to `/cowrite`. Already have an idea? `/brainstorm <your idea>` starts from there.

Resuming later, on any track, use the same command. Run `/cowrite` again; it reads the project's `progress.md` and picks up where you stopped.

## Advanced usage

`/cowrite` is the recommended path. It sequences everything below in the right order and keeps context loading invisible. If you want a single pass without the guide, drive the skills directly.

**Fiction:** `/bible-init` scaffolds the project. Drop samples in `style/samples/` and run `/style-learn`. Then `/premise`, `/character`, `/world`, `/outline`. Draft with `/scene`. Revise with `/slop-check`, `/continuity`, `/critique`. Finally `/bible-update` folds new canon back in.

**Non-fiction:** same shape, lighter. Brief and facts instead of a bible. Draft sections with `/expand` and `/continue`. Run the same revision skills after.

**Any mode:** `/line-edit`, `/slop-check`, `/prose-grade`, and `/read-aloud` are fully generic. They work on any draft, project or not.

## Layout

```
Cowriter/
├── README.md
├── brain.md                # writer-level memory, hard-capped, shared across everything below
├── .claude/skills/          # 23 Claude Code entry points (optional; thin wrappers over frameworks/)
├── frameworks/               # real method content: portable, paste-into-any-chat markdown
│   ├── core/                   # context-map.md: track loads, defined once
│   ├── guide/                   # cowrite conductor, brain, quick-track methods
│   ├── prewriting/              # premise, outline, brief/facts methods
│   ├── drafting/                # scene and section-drafting methods
│   ├── revision/                # continuity, critique, revision methods
│   ├── craft/                   # slop-markers, style-fingerprint schema
│   ├── bible/                   # bible-init/update methods (fiction canon)
│   └── nonfiction/              # nonfiction-method.md (all seven forms)
├── projects/                # non-fiction and fiction projects live here
│   └── <name>/                 # fiction: bible/ + outline.md + drafts/ · non-fiction: brief.md + facts.md + outline.md + drafts/
├── contexts/                # saved quick-track situations (an ongoing dispute, a persona)
│   └── <name>/                 # brief.md + log.md + optional style/
└── examples/test-book/      # worked fixture, kept out of projects/ so /cowrite greets new writers
```

## Run in any LLM

Cowriter is a portable method written in markdown, so you can run the entire pipeline in any chat that accepts text. You lose only the auto-loading magic. In Claude Code, the skill wrapper reads `brain.md`, detects mode marker files, and pulls the right framework section. In a plain chat, you do that driving yourself. The method is the same; the conductor's seat just moves from the wrapper to you.

### What to paste

Drop into the chat window (or the custom-instructions / system-prompt slot, if the model surfaces one) a rules block, in roughly this order:

1. [`frameworks/core/context-map.md`](frameworks/core/context-map.md): the contract. What loads per mode, which layer wins on conflict.
2. [`frameworks/guide/guide-method.md`](frameworks/guide/guide-method.md): the conductor. Its phase table tells you (and the model) what comes next.
3. `brain.md` from the repo root: standing rules and steers. Replace it with your own once you have one.
4. Whatever the current phase needs:
   - **Fiction**: [`frameworks/bible/bible-method.md`](frameworks/bible/bible-method.md), [`frameworks/prewriting/prewriting-methods.md`](frameworks/prewriting/prewriting-methods.md), [`frameworks/craft/style-fingerprint-schema.md`](frameworks/craft/style-fingerprint-schema.md), [`frameworks/prewriting/outline-method.md`](frameworks/prewriting/outline-method.md), [`frameworks/drafting/scene-method.md`](frameworks/drafting/scene-method.md), [`frameworks/revision/revision-methods.md`](frameworks/revision/revision-methods.md).
   - **Non-fiction**: [`frameworks/nonfiction/nonfiction-method.md`](frameworks/nonfiction/nonfiction-method.md).
   - **Quick**: [`frameworks/guide/quick-method.md`](frameworks/guide/quick-method.md).
   - Plus whatever project state exists so far: `brain.md`, (or `brief.md` + `facts.md`), `style/style-fingerprint.md`, `outline.md`. Paste the current state at the start of a session, and keep it in a note you edit live as you go.

The list looks long, but you only paste the files for the phase you're running. A fiction draft session loads the bible, the fingerprint, and `scene-method.md`. A critique session loads `premise.md` and `revision-methods.md`. The context-map tells the model which slot each file fills.

### Changes vs. Claude Code

- **No slash commands.** You drive the sequence by hand. Open `guide-method.md`, read the phase table, and tell the model what phase you're in ("we are Phase 5, drafting beat 4"). The model then runs the method inline.
- **No auto-loading.** When a phase says "load the fingerprint," you paste it. When `brain.md` picks up a new steer, you edit the file yourself instead of letting the wrapper persist it.
- **No skill auto-discovery.** The 23 `/skill` entry points do nothing outside Claude Code. Skip them; the framework files are the real method.
- **Everything else is identical.** The slop kill-list, style fingerprint, authority order (`style-fingerprint > style-guide > brain > slop-markers`), canon enforcement, and one-step-at-a-time conductor rules. These are all just markdown the model reads.

### Compatibility

The method is model-agnostic and uses no Claude-specific features. The framework files are plain markdown, and paste cleanly into Claude.ai, ChatGPT, Google Gemini, or any local frontend that exposes a system-prompt slot (LM Studio, Ollama Web UI, and friends). No modifications required. If the model has a small context window, paste only the files for the current phase rather than the whole stack.

## Project status

All three tracks are built, across all 23 skills.

- [x] Fiction pipeline: bible spine, prewriting, drafting, revision (the original build)
- [x] Craft floor: slop-markers, style-fingerprint schema, length budgets
- [x] Brain: writer-level memory shared across every project and context
- [x] Non-fiction track: brief/facts/outline project shape, one method for all seven forms
- [x] Quick track: zero-setup drafting, saved contexts for recurring situations

`examples/test-book/` is a worked fixture you can point `/cowrite` at to see the fiction pipeline end to end without starting your own project.

## Maintainers

[@Flametossed](https://github.com/Flametossed).

## Contributing

Issues and PRs welcome. [Open an issue](https://github.com/Flametossed/Cowriter/issues/new) for bugs or method suggestions. Framework changes should go through `frameworks/`, not `.claude/skills/*/SKILL.md` — the skill files are thin wrappers and should stay that way.

## License

[MIT](LICENSE) (c) Flametossed
</content>
