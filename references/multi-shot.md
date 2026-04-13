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

## How many shots can fit in 15 seconds?

- **2 shots** — 7.5s each, contemplative, breathing room
- **3 shots** — 5s each, standard ad pacing
- **4 shots** — ~3.75s each, punchy, fits most UGC/brand flows
- **5+ shots** — tight, risk of drift, only if each shot is <3s and visually similar

**For Pat's audience:** 3-shot in 10–12s is the sweet spot. Gives narrative room without cramming.

## Worked examples

### Example: Brand film (3-shot, seamless)
```
Target: 15 seconds, one continuous uncut shot, 16:9

Shot 1 (0–5s): A runner at dawn on a mountain trail, steam rising from their breath, golden hour backlight cutting through pine trees behind them. Camera: slow dolly-in from the front, waist height.

Shot 2 (5–10s): The camera continues pushing in as the runner speeds up, the trail narrowing into tight switchbacks, dust kicking up from each footstrike. Same runner, same outfit, same lighting direction.

Shot 3 (10–15s): The runner crests a ridge, stops, and turns to face the valley below, morning mist rolling across the peaks. Camera: continues its push until landing on a wide over-the-shoulder reveal.

One continuous uncut shot, no cuts. Style: cinematic brand film, shot on anamorphic lens, warm color grade, shallow depth of field. Smooth motion, stable framing, consistent character identity, natural light progression, no warping, no flicker.
```

### Example: Product transformation (3-shot, environment warp)
```
Target: 12 seconds, 9:16 for Reels, @Image1 = Stanley tumbler product photo

0–4s: The Stanley tumbler from @Image1 sits on a pristine modern desk, soft daylight from a left-side window, camera static wide.

4–8s: A hand enters frame and picks up the Stanley from @Image1, lifting it toward camera as the desk dissolves into a mountain trail at golden hour — same Stanley from @Image1 still in the hand, steam now rising from the lid.

8–12s: The Stanley from @Image1 sits on a granite rock, mountain range visible behind it, golden hour backlight, camera slow push-in to hero the lid.

Style: cinematic lifestyle commercial, warm color grade, shallow depth of field. Product from @Image1 identical throughout — same color, same logo, same shape. Smooth environmental transition, stable framing, consistent product identity, natural light, no warping, no flicker.
```
