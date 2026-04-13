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

## Timestamp syntax (pick one — stay consistent)

### Option A — Shot-number labeled
```
Shot 1 (0–4s): [description, camera, action]
Shot 2 (4–8s): [description, camera, action]
Shot 3 (8–12s): [description, camera, action]
```

### Option B — Time-only labeled (tighter, preferred for ads)
```
0–4s: [description]
4–8s: [description]
8–12s: [description]
```

Both work. Option A is clearer when you reference shots later in the prompt; Option B is more compact.

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

### Example: Brand film — 15s, seamless single take, 16:9
Character `@Image1` = stylized runner sheet. 10 beats of ~1.5s each.
```
A runner at dawn on a mountain trail, golden hour backlight cutting through pine trees, warm atmospheric mist.

Shot 1 (0–1.5s): Extreme close on the runner's lacing fingers tightening a shoe. Camera: locked macro. Low density.
Shot 2 (1.5–3s): Close on the runner's face from @Image1, steam rising from their breath. Camera: slow dolly-out, 6 inches.
Shot 3 (3–4.5s): Medium shot of the runner from @Image1 beginning to move, feet lifting off the trail. Camera: continues dolly-out.
Shot 4 (4.5–6s): Tracking shot alongside the runner, trail narrowing into switchbacks, dust kicking up. Camera: tracking parallel.
Shot 5 (6–7.5s): Signature beat — close on the runner's feet from @Image1 striking the trail. Stacked effects: shallow rack focus on heel strike + speed ramp (deceleration) to ~25% speed.
Shot 6 (7.5–9s): Speed ramps back to normal. Wide shot, runner small against the valley, ridge ahead.
Shot 7 (9–10.5s): Runner from @Image1 pushes up the final switchback, legs driving. Camera: low angle tracking.
Shot 8 (10.5–12s): Runner crests the ridge, silhouetted against morning light. Camera: pulls back into wider framing.
Shot 9 (12–13.5s): Runner from @Image1 stops, turns toward the valley. Camera: slow arc to over-the-shoulder.
Shot 10 (13.5–15s): Energy resolves — runner faces the valley, mist rolling across the peaks, warm light holds. Camera comes to rest wide.

One continuous uncut shot feel. Style: cinematic brand film, anamorphic lens, warm color grade, shallow depth of field. Runner from @Image1 identical throughout. Smooth motion, stable framing, natural light progression, no warping, no flicker.
```

### Example: Product transformation — 12s environment warp, 9:16 for Reels
`@Image1` = Stanley tumbler product photo. 7 beats.
```
The Stanley tumbler from @Image1 sits on a pristine modern desk, soft daylight from a left window.

Shot 1 (0–2s): Wide static on the Stanley from @Image1, desk objects around it, flat daylight. Camera: locked. Low density.
Shot 2 (2–3.5s): A hand enters frame from the right and reaches toward the Stanley from @Image1. Camera: cut to medium.
Shot 3 (3.5–5s): Hand lifts the Stanley from @Image1 off the desk toward camera. Camera: dolly-in, 6 inches.
Shot 4 (5–7s): Signature beat — as the Stanley from @Image1 moves through frame, the desk dissolves into a mountain trail at golden hour around it. Stacked effects: environment dissolve + speed ramp (deceleration) to ~50% speed through the warp.
Shot 5 (7–8.5s): Speed ramps back up. Hand places Stanley from @Image1 on a granite rock, steam rising from the lid, trail and peaks now fully established behind.
Shot 6 (8.5–10.5s): Camera dolly-in on the Stanley from @Image1, warm golden hour backlight, hero framing on the lid. Medium density.
Shot 7 (10.5–12s): Energy resolves — motion ceases, Stanley from @Image1 hero-lit on the rock, mountain range behind, warm light holds. Camera at rest.

Style: cinematic lifestyle commercial, warm color grade, shallow depth of field. Product from @Image1 identical throughout — same color, same logo, same shape. Smooth environmental transition, stable framing on the after state, consistent product identity, no warping, no flicker.
```
