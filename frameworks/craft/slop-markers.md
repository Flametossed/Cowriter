# Slop Markers — the AI-writing kill-list

> Portable quality floor. A catalog of the tells that make prose read as generic AI output, each with **detection** and **fix**. Paste this into any chat as a "do not do these" block, or let `slop-check` scan against it.

> **Authority:** this is the *floor*, the lowest-priority rule set. A book's `style-fingerprint.md` and `style-guide.md` override any marker here. If the writer's voice deliberately uses a thing on this list, the voice wins — do not flag it. Order: `fingerprint > style-guide > slop-markers`.

---

## 1. Structural crutches (highest priority — kill on sight)

- **Antithesis tic** — "It's not X, it's Y." / "Not just X, but Y." / "X isn't about Y. It's about Z."
  - *Why slop:* AI's default rhetorical reflex. One per book is a choice; three per page is a tell.
  - *Fix:* state the thing directly. Cut the negated half.

- **Triad rhythm** — endless three-item lists and three-beat sentences. "She was tired, hungry, and alone."
  - *Fix:* vary item counts. Sometimes one. Sometimes five.

- **Sentence-length monotony** — every sentence 12–18 words, subject-verb-object.
  - *Fix:* deliberately alternate. Drop a 3-word sentence after a 30-word one.

- **Repetitive openers** — paragraph after paragraph starting "She…", "The…", "As…", "With…".
  - *Fix:* check the first word of consecutive sentences; break runs.

- **"As" simultaneity overload** — "She walked as she thought as the rain fell as…"
  - *Fix:* one action at a time; let sequence breathe.

## 2. Telling instead of showing

- **Named emotions** — "She felt sad / a wave of relief / a surge of anger."
  - *Fix:* render the symptom (body, action, what she does to the world), let the reader name it.

- **Filter words** — *felt, saw, heard, noticed, watched, realized, seemed, knew, thought, wondered.* They put a camera between reader and scene.
  - *Fix:* delete the filter, state the thing. "She saw the door open" → "The door opened."

- **"Began to / started to"** — hedged action. "He began to walk."
  - *Fix:* "He walked." Use inception verbs only when the start is interrupted.

- **Stating the subtext** — dialogue followed by a line explaining what it meant.
  - *Fix:* trust the reader. Cut the explanation.

## 3. Purple / empty texture

- **Atmosphere clichés** — "the air crackled with tension," "a palpable silence," "time seemed to slow," "the tension was thick."
- **Abstraction sandwiches** — "a mix of fear and hope," "an odd sense of unease," "a strange feeling."
  - *Fix:* one concrete, specific, ownable detail beats any abstract blend.
- **Sensory boilerplate** — generic smells of rain/coffee/ozone; "salty air"; "metallic tang of blood."
  - *Fix:* pick the detail only *this* place/moment has.
- **Grandiosity** — "a testament to," "a symphony of," "a dance of," "in that moment everything changed."

## 4. Dead language

- **Cliché phrases / dead metaphors** — "heart pounded," "blood ran cold," "let out a breath," "knot in her stomach," "world came crashing down," "eyes widened."
- **The breath everyone holds** — "let out a breath she didn't know she was holding." Banned outright.
- **Eyes doing impossible things** — "her eyes fell to the floor," "his gaze swept the room and landed on…" (overused).
- **Adverb-propped dialogue tags** — "she said angrily/quietly/sharply."
  - *Fix:* let the line + action carry tone; prefer plain "said," or replace the tag with a beat.

## 5. AI-default diction (the vocabulary tells)

Overused words that flag machine prose. Flag clustering, not single use:
*delve, tapestry, testament, navigate (figurative), realm, beacon, whisper (of), dance (of), symphony, kaleidoscope, palpable, ineffable, liminal, visceral, juxtapose, myriad, plethora, nestled, bustling, gleaming, shimmering, cascade, weave/woven, underscore, evoke, resonate, embark, journey (figurative).*

## 6. Pacing / camera slop

- **Beat-by-beat blocking** — narrating every step of mundane motion (stand, cross room, reach, turn knob, open door).
  - *Fix:* cut to the meaningful beat. "She left." gets her out of the room.
- **Mirror/reflection self-description** — character conveniently catalogs their own appearance.
- **Weather-as-mood opener** — starting a scene with the sky matching the feeling.
- **Echo words** — same distinctive word twice in a paragraph (other than intentional).

---

## How `slop-check` should report

For each flagged span:
```
[category] "quoted offending text"  (file:line)
  why: <one line>
  fix: <concrete rewrite or direction>
```
End with a **density score** (markers per 1000 words) and the top 3 recurring offenders for this draft. Don't rewrite the whole passage unless asked — flag + suggest, let the writer keep control of the voice.
