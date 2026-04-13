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

For full worked prompts using these patterns, see `product-ads.md` (product + character), `multi-shot.md` (brand film), and `characters.md` (multi-character, dual-reference face+outfit). These are role-assignment snippets showing how to write the `@REFS` bullet when using multiple assets.

### Product + character (Format 2 from product-ads.md)
Uploads: `@Image1` = stylized character sheet, `@Image2` = product photo.

Per-shot `@REFS` bullet reads: `@Image1 character identity, @Image2 product shape + label`.

At end: `IDENTITY LOCK: Character from @Image1 identical. Product from @Image2 identical — same shape, label.`

### Character + location + camera reference
Uploads: `@Image1` = character, `@Image2` = location, `@Video1` = camera move reference.

Per-shot `@REFS` bullet: `@Image1 character, @Image2 environment, @Video1 for camera pacing`.

At end: `Apply camera behavior from @Video1 throughout. Character from @Image1 identical. Environment from @Image2 consistent.`

### Product + audio pacing
Uploads: `@Image1` = product, `@Audio1` = music cue.

Per-shot `@REFS` bullet: `@Image1 product, @Audio1 sets beat tempo`.

At end: `Motion and beat transitions synced to @Audio1. Product from @Image1 identical.`

### First-frame + last-frame pin
Uploads: `@Image1` = opening frame, `@Image2` = closing frame.

In SHOT 1 `@REFS`: `@Image1 pinned as first frame`. In final SHOT `@REFS`: `@Image2 pinned as final frame`.

At end: `No cuts, continuous single take. First frame matches @Image1. Final frame matches @Image2.`

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
