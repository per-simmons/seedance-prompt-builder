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

Every pattern below is beat-structured. Timestamps are mandatory — see SKILL.md's Timestamping section. Never collapse these into prose blocks.

### Pattern 1 — Product + character (Format 2 from product-ads.md), 10s example
Uploads: `@Image1` = stylized character sheet, `@Image2` = product photo.
```
Medium shot of the character from @Image1 in a modern kitchen, soft morning light from a left window.

Shot 1 (0–2s): Character from @Image1 holds the product from @Image2 at chest height, label facing camera. Camera: locked medium.
Shot 2 (2–4s): Character from @Image1 brings product from @Image2 closer, takes a small sip. Camera: 6-inch dolly-in.
Shot 3 (4–7s): Signature beat — character reacts naturally, eyes brighten. Stacked effects: focus pull from product to face + gentle speed ramp (deceleration) to ~50% speed.
Shot 4 (7–9s): Speed ramps back up, character nods approvingly. Camera: holds medium.
Shot 5 (9–10s): Energy resolves — character lowers product from @Image2 beside them, framing stable.

Character from @Image1 identical throughout — same face, hair, outfit. Product from @Image2 identical — same color, logo, shape. Smooth motion, no identity drift.
```

### Pattern 2 — Character + location + camera reference, 10s example
Uploads: `@Image1` = character sheet, `@Image2` = location photo, `@Video1` = reference video of a camera push-in.
```
The character from @Image1 stands in the environment shown in @Image2, golden hour lighting.

Shot 1 (0–2s): Character from @Image1 faces camera at medium distance in the environment from @Image2. Camera: matches the opening framing of @Video1.
Shot 2 (2–5s): Reference @Video1 for camera movement and pacing — apply the push-in motion to the character from @Image1 in this new scene. Low effect density.
Shot 3 (5–7s): Signature beat — character's face fully revealed in the push-in, environment from @Image2 soft-focused behind. Stacked effects: shallow rack focus + golden hour rim light bloom.
Shot 4 (7–10s): Energy resolves — push-in completes, character from @Image1 holds frame in hero close, lighting holds.

Character from @Image1 identical throughout. Environment from @Image2 consistent. Camera behavior referenced from @Video1. Smooth motion, no identity drift.
```

### Pattern 3 — Product + audio pacing, 8s example
Uploads: `@Image1` = product, `@Audio1` = 8-second music cue with clear beats.
```
Extreme macro on the product from @Image1, single drop of water beading at the rim, soft backlight.

Shot 1 (0–2s): Product from @Image1 at rest, water droplet forming slowly. Camera: locked macro. Match tempo to the intro of @Audio1. Low density.
Shot 2 (2–4s): Droplet grows, about to fall. Camera: slow dolly-in, 6 inches. Motion pace matches @Audio1 beat progression.
Shot 3 (4–6s): Signature beat — droplet falls and hits surface on the downbeat of @Audio1. Stacked effects: shallow rack focus + speed ramp (deceleration) to ~30% speed on impact.
Shot 4 (6–8s): Energy resolves — ripple settles, product from @Image1 holds in final hero frame. Music tails out. Camera at rest.

Product from @Image1 identical, label sharp. Motion synced to @Audio1. Smooth motion, stable framing.
```

### Pattern 4 — First-frame pin + last-frame pin, 6s example
Uploads: `@Image1` = opening frame, `@Image2` = closing frame.
```
Use @Image1 as the first frame. Use @Image2 as the final frame.

Shot 1 (0–2s): The scene from @Image1 holds briefly, subtle atmospheric motion — drifting clouds, faint breeze, ambient light. Camera: begins slow push-in.
Shot 2 (2–4s): Continued slow push-in, environment transitions gradually toward the state shown in @Image2. Low density.
Shot 3 (4–6s): Final frame settles into @Image2 exactly. Energy resolves — motion ceases, framing locks. No cut.

No cuts, continuous single take. First frame matches @Image1 exactly. Final frame matches @Image2 exactly.
```

## Double-check checklist before delivering the prompt

Most multi-reference prompts fail because of @ tag mistakes. Before outputting:

- [ ] Every uploaded asset has an @ tag referenced in the prompt.
- [ ] Every @ tag has exactly one role assigned.
- [ ] "Use" vs "Reference" is the right word for each.
- [ ] Each @ tag is re-referenced in every beat where it applies.
- [ ] Prompt uses timestamped beats (mandatory for anything ≥ 5s).
- [ ] Constraint tail includes the identity lock for characters/products.
- [ ] Upload counts are within limits (9/3/3, 12 total).

If any box is unchecked, fix before outputting.
