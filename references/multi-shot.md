# Beat Pacing & Transitions for Seedance 2.0

Load this when planning how to break a prompt into timestamped beats, choose transitions between them, and lock product/character identity across beats. Every prompt over 5 seconds uses this structure — it's the default format, not a special case.

## Contents
- Beat density by duration
- Timestamp syntax
- Transition vocabulary (every transition is a creative moment)
- Consistency across beats (product, character, environment)
- Density contrast — why beat rhythm matters
- Worked examples

## Beat density

From the Seedance prompting docs and real-world creator practice:

| Duration | Beats | Seconds per beat |
|---|---|---|
| 3–5s | 2–3 beats (or 1 if atomic) | 1–2s each |
| 5–10s | **4–7 beats** | 1–2s each |
| 10–15s | **8–12 beats** | 1–1.5s each |
| 15s (max) | 12–14 beats | 1–1.5s each |

**More, shorter beats ≫ fewer, longer ones.** Every beat is a chance to anchor a specific action, camera move, or effect for Seedance. Prose blocks without beats let the model guess pacing, and it usually rushes or skips.

The only exception: a single atomic action under 5s (e.g., a 3-second hero macro of a bottle with no character or camera motion). Everything else timestamps.

## Beat format

Follow the SKILL.md output format — multi-line SHOT bullets, not one-liners. See SKILL.md's "Output format — strict template" section for the canonical shape.

## Transition vocabulary

Seedance handles transitions natively. Specify the type you want:

| Transition | Phrasing |
|---|---|
| **Clean cut** | (Default — don't specify) |
| **Seamless / no cut** | `no cuts, continuous single take` — critical for the "one prompt, one shot" look |
| **Whip pan** | `whip pan right to left connecting shots, motion blur smear` |
| **Speed ramp** | `speed ramp from slow-motion into normal speed at the transition` |
| **Match cut** | `match cut on [matching element — hand position, product shape, light direction]` |
| **Environment warp** | `the environment dissolves from [A] into [B] around the subject` (the viral format — great for travel/lifestyle ads) |
| **Fade** | `fade to black between shots` — usually for end of video only |

If you want no cuts at all (true single-take feel), write: `one continuous uncut shot, no cuts, no end card.`

## Consistency across shots — this is the hard part

Seedance drifts on character and product identity across shots unless you explicitly lock it.

### For product identity
Reference `@Image1` in EACH shot, not just once at the top:
```
0–4s: Hero macro of the [product] from @Image1 on a studio surface...
4–8s: The [product] from @Image1 now held in a hand, walking through a mountain trail...
8–12s: Close-up of the [product] from @Image1, label legible, golden hour backlight...
```

And lock it in the constraint tail:
```
Product from @Image1 identical in every shot — same color, same logo placement, same label text.
```

### For character identity
Same pattern. Reference `@Image1 (the character sheet)` in every shot. Explicit lock in constraints:
```
Character from @Image1 identical in every shot — same face, same hair, same outfit.
```

### For environment continuity
If the action stays in one location across shots, state it once:
```
Location stays consistent across all shots — same kitchen, same lighting direction, same props in the background.
```

## Beat density (not "shots per video" — beats per video)

Forget thinking in terms of "number of shots." Think in beats. Every beat is 1–4 seconds. Every prompt is a timestamped list of beats.

- **5s prompt** → 3–4 beats
- **8s prompt** → 5–6 beats
- **10s prompt** → 5–7 beats
- **12s prompt** → 7–9 beats
- **15s prompt** → 10–12 beats

A 10-second prompt with 2 beats (5 seconds each) is NOT acceptable. Seedance needs finer anchors to pace correctly. Err toward more beats of shorter length.

## Worked examples

### Example: Brand film — 15s, single seamless take, 16:9
`@Image1` = stylized runner character sheet. 10 beats of ~1.5s each.
```
SHOT 1 (0–1.5s) — Laces
• ACTION: close on the runner's fingers tightening a shoelace
• CAMERA: locked macro
• LIGHT: golden hour backlight through pine trees
• EFFECT: none, low density
• @REFS: @Image1 runner identity

SHOT 2 (1.5–3s) — Breath
• ACTION: close on runner's face, steam rising from their breath
• CAMERA: slow dolly-out, 6 inches
• LIGHT: rim light catches breath vapor
• EFFECT: none
• @REFS: @Image1

SHOT 3 (3–4.5s) — Lift Off
• ACTION: runner begins to move, feet lifting from trail
• CAMERA: continues dolly-out
• LIGHT: unchanged
• EFFECT: none
• @REFS: @Image1

SHOT 4 (4.5–6s) — Track
• ACTION: runner moves through narrowing switchbacks, dust kicking up
• CAMERA: tracking parallel alongside runner
• LIGHT: unchanged
• EFFECT: none
• @REFS: @Image1

SHOT 5 (6–7.5s) — Heel Strike (SIGNATURE)
• ACTION: close on runner's feet striking the trail, dust burst at contact
• CAMERA: low angle, locked
• LIGHT: rim catches dust particles
• EFFECT: stacked — shallow rack focus on heel strike + speed ramp (deceleration) to ~25% speed
• @REFS: @Image1

SHOT 6 (7.5–9s) — Release
• ACTION: runner continues forward, pace picking back up
• CAMERA: wide shot, runner small against valley
• LIGHT: unchanged
• EFFECT: speed ramp (acceleration) back to normal
• @REFS: @Image1

SHOT 7 (9–10.5s) — Climb
• ACTION: runner pushes up final switchback, legs driving
• CAMERA: low-angle tracking
• LIGHT: unchanged
• EFFECT: none
• @REFS: @Image1

SHOT 8 (10.5–12s) — Crest
• ACTION: runner crests the ridge, silhouetted against morning light
• CAMERA: pulls back into wider framing
• LIGHT: warm golden hour full behind
• EFFECT: none
• @REFS: @Image1

SHOT 9 (12–13.5s) — Turn
• ACTION: runner stops, turns toward the valley
• CAMERA: slow arc to over-the-shoulder
• LIGHT: unchanged
• EFFECT: none
• @REFS: @Image1

SHOT 10 (13.5–15s) — Resolve
• ACTION: runner faces the valley, mist rolling across peaks
• CAMERA: comes to rest wide
• LIGHT: warm light holds
• EFFECT: none
• @REFS: @Image1

STYLE: cinematic brand film, anamorphic lens, warm color grade, shallow depth of field
IDENTITY LOCK: Runner from @Image1 identical throughout
CONSTRAINTS: smooth motion, stable framing, natural light progression, no warping, no flicker
```

For a product-transformation example (environment warp), see `product-ads.md` → Stanley tumbler worked example.
