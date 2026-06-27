# Brainstorm (Cowriter's ideation stage)

The **ideation stage** of [Cowriter](../README.md) — the part that comes *before* you write. Formerly the standalone *Brainstormer* tool, now nested inside the Cowriter workspace: brainstorm finds the idea, Cowriter writes the book. Run `/brainstorm` from the Cowriter workspace; when the concept locks, its `handoff` writes the premise + outline into `../projects/<book>/` and `/cowrite` resumes from there — same workspace, no repo switch.

It exists to fix the one thing AI is worst at in fiction: **originality of concept.** Ask an AI for a story and it returns the statistical center of everything it has read — the chosen one, the ancient evil, the mentor who dies at the midpoint. Brainstormer pulls the idea *off that center* on purpose, while keeping it coherent and writable, by working *with* the writer instead of generating *at* them.

## What it does

1. **Diverges** — generates many raw, specific, writer-rooted sparks before judging any. Quantity first.
2. **Twists** — takes a chosen spark and makes it un-AI: names the default version, then subverts one axis.
3. **Pressure-tests** — runs a **trope kill-list** (the idea-level analog of Cowriter's slop-markers) and a set of **originality tests** against the concept.
4. **Builds the spine** — a testable premise, an original plot engine, and a beat sketch that subverts the predictable turns.
5. **Hands off** — writes the finished premise and outline straight into Cowriter so `/cowrite` resumes from there.

## How it's meant to be used

Everything here is **dual-use**, exactly like Cowriter:

- **As a Claude Code skill** — run `/brainstorm` from the Cowriter workspace (the command lives in Cowriter's `.claude/skills/`). It's the single front door; the conductor drives the specialist methods (`spark`, `twist`, `plot`, `beats`, `trope-check`, `seed`, `handoff`) inline — you don't invoke them separately. Their wrappers are carried under `.claude/skills/` here for reference and portability.
- **As a portable prompt library** — the real method content lives in `frameworks/` as plain Markdown. Paste any of it into any AI chat as a rules/context block. The `.claude/skills/*/SKILL.md` files are thin wrappers that point at these frameworks — no duplicated content.

## Start here: `/brainstorm`

**The front door.** You don't need to learn the skill names. Run:

```
/brainstorm
```

It detects where your session is, then walks you through it one step at a time — diverge → twist → premise → plot → beats → handoff — routing to the right tool automatically and keeping a live session log so you can stop and resume. When the concept is locked, it writes the premise + outline into `../projects/<book>/` and you keep going with `/cowrite` — same workspace.

**Already have an idea?** Hand it over and start from there:

```
/seed a detective who can only solve crimes she was asleep during
```

(or `/brainstorm <idea>`). Seed mode skips the blank-page pile — it classifies how developed your idea is, **names the default it's sitting on** (most "I've got an idea" ideas are quietly chosen-one-shaped), and guides you into twisting and sharpening it. It skips the pile, never the originality gate.

## Layout

```
Cowriter/                    # the writing workspace (the parent)
├── .claude/skills/brainstorm/  # the /brainstorm front-door command
├── projects/                #   handoff target — your books land here
└── brainstorm/              # THIS — the ideation stage
    ├── README.md
    ├── .claude/skills/      #   carried skill wrappers (driven by the guide)
    ├── frameworks/          #   PORTABLE method content (the real meat)
    │   ├── guide/           #     the conductor
    │   ├── ideation/        #     spark, twist, plot, beat methods
    │   ├── craft/           #     trope kill-list + originality tests
    │   └── handoff/         #     how to write into ../projects/<book>/
    ├── templates/           #   blank scaffolds (the session log)
    └── sessions/            #   your brainstorm logs live here
```

> The `/brainstorm` command lives in the parent Cowriter `.claude/skills/`; the method content lives here. The conductor runs the specialist methods inline — you drive it all through `/brainstorm`.

## The originality stack (how conflicts resolve)

When skills judge an idea, they resolve in this order — the mirror of Cowriter's three sources of authority:

```
writer's intent (a trope chosen on purpose)
   > fresh angle (a default with a genuine new axis)
      > trope-slop (generic idea floor — flag the unexamined default)
```

A trope isn't slop. The *unexamined default* is. If the writer reaches for the chosen one **knowingly, with an angle**, intent wins and Brainstormer doesn't flag it. The kill-list only catches the reflex.

## Divergence vs. convergence (the one rule that matters)

Brainstormer keeps the two motions **separate**, because mixing them is how good ideas die young:

- **Diverge** (Spark): make many, judge none. Defer all criticism. Quantity, specificity, weirdness.
- **Converge** (Twist → Premise → Plot → Beats): now judge hard. Cut, sharpen, pressure-test.

The conductor never lets you criticize during divergence or daydream during convergence.

## Full skill list

| Phase | Skills |
|-------|--------|
| **Guide (start here)** | **`brainstorm`** — conducts all of the below |
| Start with an idea | `seed` — begin from a premise/vibe you already have (or `/brainstorm <idea>`) |
| Diverge | `spark` — generate many raw concepts |
| Converge | `twist` — make a spark original · `plot` — build the plot engine · `beats` — subvert the turns |
| Quality | `trope-check` — scan an idea against the kill-list |
| Handoff | `handoff` — write premise + outline into `../projects/<book>/` |

## Relationship to Cowriter

The brainstorm stage **ends** where Cowriter's `/premise` and `/outline` *would* start from a blank seed. Instead of arriving at the drafting stage with a vague vibe, the writer arrives with a pressure-tested, original premise and beat sketch already in `../projects/<book>/`. From there, `/cowrite` takes over: characters, voice, drafting, revision — same workspace, no repo switch.
