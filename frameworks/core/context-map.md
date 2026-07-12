# Context Map — what to load, per mode

> Portable. Every drafting and revision method loads its working context through this map instead of hard-coding fiction paths. The **Fiction column reproduces the classic Cowriter stack exactly**, so fiction behavior never changes; the other columns are the same slots filled by lighter files.

## Resolution procedure (run before any drafting/revision work)

1. **Brain first** — load `brain.md` at workspace root ([brain-method.md](../guide/brain-method.md)). Its Writer/Steers lines are standing constraints; its Efficiency directives may prune anything loaded below.
2. **Find the active workspace**, in priority order:
   - a project/context the writer named →  use it;
   - the single project/context already active in this conversation;
   - a saved quick context in `contexts/<name>/` that matches the ask;
   - none → this is a pure **quick task**: the context is whatever brief was gathered in-chat (audience / goal / tone).
3. **Read the mode from marker files** — never ask: `bible/` present → **fiction**; `brief.md` present at project root → **non-fiction**; lives under `contexts/` → **quick (saved context)**.
4. **Load the mode's stack** from the table below.
5. **Apply brain Efficiency directives** to prune the stack (e.g. "fingerprint locked — never reload samples").

## The mode table

| Slot | Fiction (`projects/<book>/`) | Non-fiction (`projects/<name>/`) | Quick |
|------|------------------------------|----------------------------------|-------|
| **Facts / canon** | `bible/canon-facts.md` + relevant `characters.md` / `world.md` entries | `facts.md` (numbered claims + sources) | none |
| **Purpose** | `bible/premise.md` | `brief.md` (thesis, audience, goal, form, tone) | in-chat brief, or `contexts/<name>/brief.md` + `log.md` |
| **Structure** | `outline.md` beats + tiers/budgets | `outline.md` sections + budgets | none |
| **Voice** | `style/style-fingerprint.md` → `style/style-guide.md` | same | `contexts/<name>/style/` if saved, else brain writer-defaults |
| **Quality floor** | [slop-markers.md](../craft/slop-markers.md) minus the book's exceptions | same, minus the project's exceptions | same, minus brain exceptions |

## Authority on conflict (all modes)

`style-fingerprint > style-guide > brain (writer defaults) > slop-markers`.
The Facts/canon slot is **never** overridden by style, brain, or the creativity dial — in fiction that's the bible; in non-fiction it's `facts.md`; a quick task has no locked facts beyond what the writer stated.

## Notes

- **What each slot means per mode:** "continuity" checks the Facts slot (bible in fiction, claim/source list in non-fiction). "Voice drift" always means drift from the Voice slot. Methods that name `bible/…` paths are describing the fiction column.
- Skills that only exist for fiction (`bible-*`, `premise`, `character`, `world`, `outline`, `continuity`, `scene`, `brainstorm`) simply aren't offered outside the fiction track.
- A quick task never creates files. A **saved context** (`contexts/<name>/`) holds only `brief.md` (situation, audience, my position, tone, do/don't), optional `style/`, and `log.md` (one line per piece sent). See [quick-method.md](../guide/quick-method.md).
