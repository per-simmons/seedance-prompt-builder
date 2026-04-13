# @ Reference Syntax for Seedance 2.0

Load this when the user is uploading more than one reference (multiple images, videos, or audio clips) and needs them orchestrated correctly.

## Contents
- The @ tag system
- Max upload limits
- Role assignment syntax
- "Use" vs "Reference" distinction
- Common multi-reference patterns
- Double-check checklist

## The @ tag system

When the user uploads files to Seedance (via Higgsfield, Dreamina, etc.), the platform auto-assigns tags:
- `@Image1`, `@Image2`, ..., `@Image9`
- `@Video1`, `@Video2`, `@Video3`
- `@Audio1`, `@Audio2`, `@Audio3`

**You must reference each tag in the prompt AND assign it a specific role.** Seedance doesn't guess what to do with uploaded assets. It waits for you to tell it.

## Upload limits

Hard caps (from ByteDance's spec):
- **9 images** max
- **3 videos** max, ≤15 seconds each
- **3 audio clips** max, ≤15 seconds each
- **12 total references** in a single generation

Trim reference videos to only the key segment — short clean references outperform long busy ones.

## Role assignment — the five jobs

Every uploaded asset needs exactly one role. The five jobs Seedance understands:

| Role | Example phrasing | What it does |
|---|---|---|
| **First frame (pin)** | `Use @Image1 as the first frame.` | Forces the shot to start from this exact image. |
| **Last frame (pin)** | `Use @Image2 as the final frame.` | Forces the shot to end here. |
| **Style reference** | `Reference @Image3 for color palette and lighting only.` | Borrows mood without forcing geometry. |
| **Subject / character** | `The woman in @Image1 as the lead character.` | Locks character identity. Needs 2K+ resolution. |
| **Product / object** | `Reference @Image2 for product shape, label, and material. Keep it identical.` | Locks product identity across shots. |
| **Camera reference** | `Reference @Video1 for camera movement and pacing.` | Copies the camera behavior from the reference. |
| **Action reference** | `Mimic the body motion and blocking from @Video1.` | Copies the subject's action. |
| **Audio (music)** | `@Audio1 as background music.` | Uses the audio track as a BGM. |
| **Audio (pacing)** | `Match scene pacing to the beat of @Audio1.` | Cuts and motion sync to audio. |
| **Video extension** | `Extend @Video1 by 8 seconds.` | Continues an existing video from its last frame. |

## "Use" vs "Reference" — quote exactly

This distinction matters:
- **`Use @Image1 as the first frame`** → pins the exact frame. The generation MUST begin from this image.
- **`Reference @Image1 for [attribute]`** → borrows the attribute (style, product shape, etc.) WITHOUT forcing the frame.

Wrong phrasing causes wrong behavior. If you see drift on a product, check whether you wrote "use" when you meant "reference" or vice versa.

## Common multi-reference patterns

### Pattern 1 — Product + character (Format 2 from product-ads.md)
```
Uploads: @Image1 = stylized character sheet, @Image2 = product photo

"Medium shot of the character from @Image1 holding the product referenced from @Image2
in a modern kitchen, soft morning light. She takes a sip and reacts naturally.
Character from @Image1 identical — same face, same hair, same outfit.
Product from @Image2 identical — same color, same logo placement."
```

### Pattern 2 — Character + location + camera reference
```
Uploads: @Image1 = character sheet, @Image2 = location photo, @Video1 = reference video of a camera push-in

"The character from @Image1 stands in the environment shown in @Image2, golden hour lighting.
Reference @Video1 for camera movement and pacing — use the push-in motion but apply it to this
new subject and scene. Character from @Image1 identical throughout."
```

### Pattern 3 — Product + audio pacing
```
Uploads: @Image1 = product, @Audio1 = a 10-second music cue

"Extreme macro of the [product] from @Image1, a single drop of water beading at the rim.
Match scene pacing and motion to the beat of @Audio1. Camera: slow dolly-in.
Product from @Image1 identical, label sharp. Smooth motion, stable framing."
```

### Pattern 4 — First-frame pin + last-frame pin
```
Uploads: @Image1 = opening frame, @Image2 = closing frame

"Use @Image1 as the first frame. Use @Image2 as the final frame. Generate the in-between
motion as a single continuous push-in with natural atmospheric motion — drifting clouds,
gentle breeze, ambient light shift. No cuts."
```

## Double-check checklist before delivering the prompt

Most multi-reference prompts fail because of @ tag mistakes. Before outputting:

- [ ] Every uploaded asset has an @ tag referenced in the prompt.
- [ ] Every @ tag has exactly one role assigned.
- [ ] "Use" vs "Reference" is the right word for each.
- [ ] For multi-shot prompts, each @ tag is re-referenced in each shot where it applies.
- [ ] Constraint tail includes the identity lock for characters/products.
- [ ] Upload counts are within limits (9/3/3, 12 total).

If any box is unchecked, fix before outputting.
