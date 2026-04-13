---
name: seedance-prompt-builder
description: Writes paste-ready Seedance 2.0 video prompts as timestamped shot lists (1–2 second beats) — never as single prose paragraphs. Use whenever the user wants a Seedance prompt, plan a shot, build a product ad, create a brand film, animate a scene, or mentions Seedance, Higgsfield, ByteDance video, or AI video generation. Also trigger when the user describes a visual sequence, ad concept, character action, product demo, or any video they want turned into a generation-ready prompt — even without saying "Seedance." Trigger phrases include "write a video prompt", "Seedance prompt", "make a video of", "animate this", "product ad with AI video", "turn this product photo into a video", "shot list for Seedance", or any brief that needs to become a video generation prompt.
---

# Seedance 2.0 Prompt Builder

## 🚨 MANDATORY OUTPUT FORMAT — READ FIRST 🚨

**Every prompt you output is a timestamped shot list with 1–2 second beats.** Not a single prose paragraph. Not a block of description. A numbered list of timed beats: `Shot 1 (0–2s): …` `Shot 2 (2–4s): …` etc.

Rules that are not negotiable:
- 5–10s prompt = 4–7 beats, 1–2s each
- 10–15s prompt = 8–12 beats, 1–2s each
- Never stack beats longer than 2 seconds except in single atomic sub-5s clips
- If you're about to write a prose prompt, stop — convert to beats before outputting
- Every reference file in this skill (product-ads.md, multi-shot.md, etc.) uses timestamped beats. Do not collapse them into prose.

This is the #1 source of Seedance quality. Skip this rule and the generation paces badly.

---

Write paste-ready prompts for ByteDance's Seedance 2.0 video model (as accessed via Higgsfield, Dreamina, CapCut, Arcads, or the official API).

## What goes into Seedance — and what doesn't

Only the prompt text and any uploaded references (@Image1, @Video1, @Audio1) go into Seedance. Do NOT generate effects inventories, density maps, energy arcs, or director's breakdowns unless the user explicitly asks for planning notes. Rourke Heath's original skill generated four planning sections — only the shot timeline was actually usable. This skill outputs a single paste-ready prompt by default.

## Workflow

1. Read the user's brief.
2. If the brief is too vague to build a full prompt (e.g. "make something cool"), ask ONE focused clarifying question. Otherwise proceed.
3. **Break the video into timestamped beats (1–2 seconds each).** This is not optional — every prompt longer than 5 seconds is a timestamped shot list. See "Timestamping" below.
4. If the brief involves a specific use case, load the matching reference file:
   - **Product ads / UGC / ecommerce** → read `references/product-ads.md`
   - **Beat pacing, transitions, per-beat identity locking** → read `references/multi-shot.md`
   - **Multiple uploaded images/videos/audio** → read `references/references-syntax.md`
   - **Character consistency across shots** → read `references/characters.md`
   - **Complex camera choreography** → read `references/camera-moves.md`
5. Build the prompt using the 6-step formula below, applied to each beat.
6. Output in the format specified under "Output format."

## The 6-step formula

Every prompt follows this structure:

```
[Subject], [Action], in [Environment], camera [Camera], style [Style], avoid [Constraints]
```

- **Subject** — who or what. Be specific: "a 35-year-old barista with curly auburn hair in a denim apron" beats "a woman."
- **Action** — one verb per shot, with quantified intensity. "slowly pours steamed milk into a latte, tracing a rosetta" beats "makes coffee."
- **Environment** — location AND lighting. Lighting is the single highest-impact element in any Seedance prompt.
- **Camera** — exactly ONE primary camera instruction per shot. Multiple camera moves cause jitter.
- **Style** — one strong visual anchor. Prefer "shot on 35mm Kodak Portra" over stacking "cinematic, beautiful, epic, amazing."
- **Constraints** — positive-phrased quality guardrails (e.g. "smooth motion, stable framing, natural skin tones"). See the Constraints section below.

**Target length: 60–100 words.** Too short = missing info. Too long = Seedance ignores details.

## Critical rules (verified against ByteDance / Higgsfield / creator docs)

### Rule 1 — One camera instruction per shot
Multiple conflicting camera moves ("dolly-in WHILE pan WHILE orbit") produce jittery, incoherent footage. Pick one primary move per shot. If you need compound motion, split into two shots with timestamps (see `references/multi-shot.md`).

### Rule 2 — Lighting is the #1 quality driver
A single precise lighting line outperforms ten generic style adjectives. Use real cinematography language: `golden hour backlight`, `hard overhead stage key`, `soft north-window daylight`, `warm 3200K practicals`, `volumetric god rays through dust`, `neon wash from storefront signage`.

### Rule 3 — "Fast" is the most dangerous keyword
Unqualified "fast" causes total quality degradation — flicker, warp, identity drift. If you need speed, pick ONE element to be fast (motion OR camera OR cuts — never all three) and describe it physically: "the runner sprints past at sprint pace, tires of the background bike streaking into motion blur."

### Rule 4 — Seedance has no true negative prompts
There is no `--no cartoon` syntax. What works: **positive constraint statements**. Instead of "no 3D, no cartoon," write `ultra-realistic, photographic, 35mm film texture`. Instead of "no wobble," write `smooth stabilized motion, stable framing`. The creator-convention phrases like `avoid jitter`, `avoid identity drift`, `avoid bent limbs` parse as positive constraints Seedance respects — they're not a negative-prompt system.

### Rule 5 — Identifiable real-face photos are blocked at upload
Seedance's content scanner rejects realistic human face references before your prompt is processed. It's an upload-time block, not a generation-time fail. Workarounds that do work: character sheets with stylized faces, product shots, obscured faces, back-of-head shots, silhouettes, hands-only framing, or text-only prompts for human subjects.

### Rule 6 — One shot, one verb
Stacking motion verbs in a single shot ("she walks, turns, jumps, waves, smiles") produces confused output. Use one verb per shot. For multiple actions, use multi-shot syntax.

### Rule 7 — Reference videos should be short
Trim reference videos to the key segment only. A 3-second clean reference outperforms a 10-second busy one.

### Rule 8 — Quantify everything
Numbers beat adjectives. `the frame rotates 15–20° clockwise over 2 seconds` lands cleaner than `the camera tilts a bit`. `approximately 20–25% speed` lands cleaner than `slow motion`. `1–2 feet of dolly movement` lands cleaner than `camera moves in`. Whenever you can put a number on a movement, an angle, a speed, or a distance, put one on it.

### Rule 9 — Contrast drives impact
Alternate beat density. A slow-motion beat hits harder right after a speed-ramped one. A clean locked-off shot feels weightier right after a handheld one. Don't stack two high-density beats back-to-back — the second one disappears. Plan beats in patterns like `high → low → high → low` or `build → peak → resolve`.

### Rule 10 — Every prompt has one signature moment
Before finalizing, identify the single beat that's the "hero" — the most visually distinctive moment, the one people will re-watch. Mark it explicitly in the prompt with phrasing like `This is the signature beat:` or `Signature moment —`. If you can't identify one, the prompt isn't strong enough yet; revise.

### Rule 11 — Energy must resolve
No matter how intense the opening beats, the final 20–30% of the video should land calmly. Effects withdraw, motion slows, the frame settles. A chaotic ending feels like the generation ran out of budget. An intentional resolution feels directed.

## Named effects vocabulary

Seedance responds better to precise effect names than generic language. When the brief calls for an effect, use these exact phrases:

**Speed & time**
- `speed ramp (deceleration)` — normal → slow-mo
- `speed ramp (acceleration)` — slow-mo → normal
- `slow motion, approximately 20–25% speed` — locked slow
- `stroboscopic / multi-exposure clone` — subject duplicated across positions in a single frame
- `freeze frame, motion hold` — single paused moment

**Camera scale**
- `digital zoom (scale-in)` — aggressive push-in
- `digital zoom (scale-out / pull-back)` — pull-back reveal
- `zoom pump` — quick scale in-and-out pulse for impact
- `dolly-in, 1–2 feet` — physical-feeling move in
- `dolly-out` — physical-feeling move out
- `orbit / arc, 30–180°` — circle around subject

**Camera motion**
- `whip pan, right-to-left` (or opposite) — fast pan with motion blur smear
- `tracking shot, parallel to subject`
- `handheld, subtle natural shake`
- `fixed / locked-off`
- `frame rotation, 15–20° clockwise` (or counterclockwise)
- `Dutch angle, 20–30° tilt`

**Light & atmosphere**
- `bloom flash, overexposed white highlights`
- `volumetric god rays through [dust / mist / window]`
- `lens flare, anamorphic horizontal streak`
- `focus pull / rack focus`
- `motion blur streak at [fast-moving element]`

**Transitions (treat each as its own moment)**
- `whip pan into next beat` — motion blur smear connecting shots
- `bloom flash into next beat` — overexposed white wipe
- `match cut on [repeated element]` — visual rhyme
- `speed ramp into next beat`
- `environment dissolve` — one location morphs into another around the subject
- `no cut, continuous single take`

When a beat stacks 2–3 of these simultaneously, mark it `stacked effects` in the prompt (e.g., `bloom flash + digital zoom scale-in + subtle camera shake — stacked effects, the signature beat`).

## The @ reference system (quick version)

When the user uploads files, Seedance auto-tags them `@Image1`, `@Image2`, `@Video1`, `@Audio1`, etc. You must reference each tag in the prompt AND assign it a specific role. Max: 9 images + 3 videos (≤15s each) + 3 audio (≤15s each) = 12 references total.

**Assigning roles — quote these exact patterns:**
- `Use @Image1 as the first frame.`
- `Reference @Image2 for outfit and product details only.`
- `Reference @Video1 for camera movement and pacing.`
- `@Audio1 as background music.`

**"Use" vs "Reference":** "Use as first frame" pins the frame exactly. "Reference" borrows the visual idea without forcing the frame.

For multi-reference prompts or character locking, read `references/references-syntax.md` and `references/characters.md`.

## Timestamping — the mandatory default

**Every prompt longer than 5 seconds is a timestamped shot list.** Not a prose block. Not a single continuous description. A list of 1–2 second beats, each with its own number, timestamp, and action.

This is how Rourke Heath prompts and how the official Seedance docs recommend structuring anything longer than a few seconds. Beats get better pacing fidelity than prose because Seedance uses them as scene anchors that pin exactly when each action should start and end. Prose prompts leave the model to guess timing, and it often rushes or skips beats.

### Duration → beat count

| Video length | Beats | Seconds per beat |
|---|---|---|
| 3–5s | 2–3 beats | 1–2s each (or a single beat if the action is truly atomic) |
| 5–10s | **4–7 beats** | 1–2s each |
| 10–15s | **8–12 beats** | 1–2s each |
| 15s (max) | 12–14 beats | 1–1.5s each |

The Hoka brand film reference (21 seconds) is broken into 14 shots at 1–2 seconds each. Apply the same density: **more, shorter beats beats fewer, longer ones.** Every beat is a chance to anchor a specific action, camera move, or effect.

### Beat format

```
Shot N (Xs–Ys): [one visible action, one camera behavior, one lighting/effect note]
```

Each beat must have:
- **One action verb** — not a list of things happening simultaneously
- **One camera instruction** — dolly-in, handheld, fixed, orbit, etc. (or "continuing previous" if it's a single continuous move across beats)
- **A lighting/effect note where it matters** — lighting shifts, effect entries, atmospheric changes
- **@references where they apply** — re-reference `@Image1` in every beat the product/character appears in

### When NOT to timestamp

Only one case: the entire clip is a single atomic action under 5 seconds (e.g., a 3-second hero macro of a bottle with no character or camera motion). Everything else gets timestamped.

## Output format

Always structure the output like this:

```
# Seedance 2.0 Prompt

**Target duration:** [X] seconds
**References to upload:** [list any @Image/@Video/@Audio the user needs to upload, or "text-only"]

## Prompt (copy this into Seedance)

```
[Opening scene-setting sentence — subject, environment, lighting.]

Shot 1 (0–Xs): [action, camera, effect/lighting note]
Shot 2 (Xs–Ys): [action, camera, effect/lighting note]
Shot 3 (Ys–Zs): [action, camera, effect/lighting note]
...

[Closing line with overall camera arc if applicable, style anchor, @reference role locks, and the positive-constraint tail.]
```

**Duration setting in Higgsfield:** [X seconds]
**Aspect ratio:** [16:9 / 9:16 / 1:1 — match brief or default to 16:9]
```

Only add a "Director's notes" section at the bottom if the user explicitly asks for planning, effects breakdown, or a shot-by-shot inventory. Default output is prompt-only.

## Constraints: the reliable positive-constraint tail

Append one concise constraint clause at the end of every prompt. Use this as the base template and adapt:

> `smooth stable framing, natural motion, consistent character identity, 4K detail, photographic realism, no temporal flicker, no bent limbs, no warping.`

Pare this down for stylized/animated prompts. For anime or illustrated styles, replace "photographic realism" with the appropriate anchor.

## Duration calibration

- **3–5 seconds:** 2–3 beats if the action has stages, or a single beat if it's atomic (pure macro, no character motion).
- **5–10 seconds:** 4–7 beats, each 1–2s. This is the most common range.
- **10–15 seconds:** 8–12 beats, each 1–1.5s. Full three-act arc (build → peak → resolve) fits comfortably here.
- **Past 15s:** Seedance generates per-shot up to 15s. For longer videos, generate multiple clips and stitch in post.

**Default to 15 seconds if the user doesn't specify.** This gives beat structure room to breathe and lands in Seedance's sweet spot.

## Clarifying questions — only when genuinely stuck

If the brief is workable, don't interrogate. Only ask ONE question if a critical element is missing. Priority of what to ask:

1. If no duration given: assume 10s and note the assumption.
2. If no aspect ratio given: assume 16:9 unless the context obviously points elsewhere (a TikTok UGC brief → 9:16).
3. If no lighting given: make a choice based on mood and state it in the prompt.
4. Only ask if the subject itself is unclear: "Is this a product demo or a person-led ad?"

## Short end-to-end example

**User:** "10-second UGC ad for a protein bar. Young woman eating it in a kitchen."

**Assistant output:**

```
# Seedance 2.0 Prompt

**Target duration:** 10 seconds
**References to upload:** @Image1 (product photo of the protein bar). If you want a specific creator likeness, generate a stylized character sheet first (Nano Banana or Midjourney) — real face photos are blocked at upload.

## Prompt (copy this into Seedance)

A woman in her late twenties in a bright modern kitchen, soft morning light pouring through a north-facing window from camera-left, warm skin tones, lightly imperfect handheld framing.

Shot 1 (0–2s): The woman holds the protein bar from @Image1 at chest height, label facing camera, casually noticing it. Camera: handheld medium, subtle natural shake.

Shot 2 (2–4s): She peels the wrapper halfway down, the motion unhurried, the wrapper from @Image1 staying clean and legible. Camera: continuing handheld, 1-foot dolly-in toward her hands. Low effect density.

Shot 3 (4–6s): Signature beat — she takes the first slow bite, eyes closing briefly on the taste. Stacked effects: shallow rack focus pulling from the wrapper to her face + gentle speed ramp (deceleration) to approximately 50% speed during the bite.

Shot 4 (6–8s): Speed ramps back up to normal. Her expression shifts from curious to pleased, a small smile breaks. Camera: continuing handheld, settling back out to medium framing.

Shot 5 (8–10s): She lowers the bar into frame beside her, wrapper from @Image1 still legible, turns slightly and nods at something off-camera. Energy resolves — handheld motion calms, framing stabilizes, warm soft light holds.

Style: iPhone UGC aesthetic, natural daylight, warm amber skin tones, 35mm film-like texture. Product wrapper from @Image1 identical throughout — same color, same logo, same text. Smooth handheld motion, stable framing through signature beat, natural skin tones, photographic realism, no warping, no identity drift, no flicker.

**Duration setting in Higgsfield:** 10 seconds
**Aspect ratio:** 9:16 (UGC default)
```

This example shows the full pattern: opening scene-setting sentence, 5 timestamped beats of 1–2s each, one action verb per beat, one camera instruction per beat (plus continuity notes), quantified numbers (1-foot dolly, 50% speed), explicit signature beat with stacked effects called out, density contrast (low → signature → resolve), per-beat @reference re-locking, and the positive-constraint tail.
