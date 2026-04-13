# Character Consistency in Seedance 2.0

Load this when the user wants a recurring character across multiple shots, a specific person-likeness (within Seedance's face-restriction rules), or is hitting drift/morphing issues.

## Contents
- The face-upload restriction (upfront)
- Character sheet best practices
- Locking identity across shots
- Multi-character setups
- Fixing morphing / drift

## The face-upload restriction — read this first

**Identifiable real-face photos are blocked at image upload.** Seedance's content scanner rejects them before the prompt is even processed. This is platform-enforced, not a prompt-engineering problem. No prompt trick bypasses it.

What you CAN upload:
- Stylized / illustrated character sheets (Nano Banana, Midjourney, Flux outputs)
- 3D / game-asset-style characters
- Obscured or partial-face images (back of head, hair over face, profile, silhouette)
- Masked-face images (sunglasses, scarf, hat brim shadow)
- Non-identifiable crowd shots
- Product-only or hands-only images

What you CANNOT upload:
- A photograph of a real person's face
- A screenshot of a celebrity
- A selfie the user took of themselves
- Any realistic image where a face is clearly identifiable

If the user needs a specific human likeness in their ad, the workflow is:
1. Generate a character sheet in an image model first (Nano Banana, Flux, Midjourney).
2. Use that character sheet as `@Image1` in Seedance.

## Character sheet best practices

When creating or accepting a character sheet for use as `@Image1`:

- **Resolution:** 2K or higher. Low-res → drift.
- **Framing:** Full body, neutral pose, plain background. Gives Seedance clean feature data to lock onto.
- **Outfit:** Single clear outfit. Avoid accessory stacking (1–2 accessories max).
- **Face:** Full-front or 3/4 view, neutral expression, clear features.
- **Lighting:** Even, flat lighting on the sheet itself. Specific lighting for the target scene goes in the prompt.
- **Style:** Whatever's legible to Seedance's scanner — stylized illustration, 3D render, semi-realistic but not photographic.

Include multiple angles if possible:
- Front full body
- Side profile
- Back or 3/4 back
- Face close-up

You can upload up to 9 images, so put several angles in as `@Image1` through `@Image4` and reference all of them:
```
Reference @Image1, @Image2, @Image3 for character identity. Character is identical
across all shots — same face, same hair, same outfit.
```

## Locking identity across shots

Three mechanisms, use all three together:

### 1. Per-shot @ reference
Mention `@Image1` in every individual shot description, not just at the top.

### 2. Explicit identity instruction
```
Character from @Image1 must stay identical. Same face, same hair, same outfit, same
build. No changes to appearance across shots.
```

### 3. Positive constraint tail
```
...consistent character identity, no identity drift, no warping, natural facial features.
```

All three combined: substantially reduces drift. Any one alone: drift happens.

## Multi-character setups

**Hard cap: 1–2 characters per generation.** Three or more causes identity confusion.

For two characters, assign explicit roles using the SKILL.md format. 10s example:
```
SHOT 1 (0–2s) — Sit
• ACTION: woman sits across from man at coffee shop table, product between them
• CAMERA: locked medium
• LIGHT: soft morning light from window
• EFFECT: none
• @REFS: @Image1 woman, @Image2 man, @Image3 product

SHOT 2 (2–4s) — Hand Off
• ACTION: woman picks up product and hands it to the man
• CAMERA: slow dolly-in, 6 inches
• LIGHT: unchanged
• EFFECT: none
• @REFS: @Image1, @Image2, @Image3

SHOT 3 (4–7s) — Reaction (SIGNATURE)
• ACTION: man takes product, examines it, reacts naturally
• CAMERA: holds medium
• LIGHT: unchanged
• EFFECT: stacked — focus pull from woman to man + speed ramp (deceleration) to ~50% speed
• @REFS: @Image2 man face clear, @Image3 product visible

SHOT 4 (7–10s) — Resolve
• ACTION: both share a knowing look, natural rest pose
• CAMERA: settles to wider medium
• LIGHT: unchanged
• EFFECT: speed ramp back to normal
• @REFS: @Image1, @Image2

STYLE: cinematic product testimonial, soft morning daylight, warm skin tones
IDENTITY LOCK: Woman from @Image1, man from @Image2, product from @Image3 identical throughout
CONSTRAINTS: smooth motion, no identity drift on either character, no warping
```

If the creative NEEDS 3+ characters, split into multiple generations:
- Generation 1: Two characters set up the scene (timestamped beats)
- Generation 2: The third character enters from their POV (timestamped beats)
- Stitch in post

## Fixing morphing / drift

Common drift symptoms and fixes:

| Symptom | Fix |
|---|---|
| Face morphs between shots | Use 2K+ character sheet. Re-reference @Image1 in each shot. Add identity lock in constraint tail. |
| Outfit changes | Explicit outfit line: `She wears exactly the outfit shown in @Image1 — [describe: e.g., navy denim jacket over a white tee].` |
| Product drifts | See `product-ads.md` — same pattern as character identity. |
| Background elements drift | State environment continuity: `Location stays consistent — same kitchen, same lighting, same props.` |
| Simple features change (hair color, glasses) | Describe them in prose in the prompt — don't just rely on the image. Seedance weights prose text heavily. |

## One uncommon trick: dual reference for identity + outfit

If the character's outfit matters (fashion, uniforms), split the reference. `@Image1` = face sheet, `@Image2` = outfit reference. 8s example:
```
SHOT 1 (0–2s) — Enter
• ACTION: character walks into frame at sunlit park
• CAMERA: tracking alongside, medium
• LIGHT: warm golden hour sidelight
• EFFECT: none
• @REFS: @Image1 face, @Image2 outfit

SHOT 2 (2–4s) — Turn
• ACTION: character turns slightly, outfit catches sidelight
• CAMERA: continues tracking, 6-inch dolly-in
• LIGHT: sidelight highlights fabric texture
• EFFECT: none
• @REFS: @Image2 outfit details clear

SHOT 3 (4–6s) — Pause (SIGNATURE)
• ACTION: character stops, holds a small pose
• CAMERA: settles to locked medium
• LIGHT: face from @Image1 fully lit
• EFFECT: stacked — shallow rack focus + speed ramp (deceleration) to ~60% speed
• @REFS: @Image1 face clear

SHOT 4 (6–8s) — Continue
• ACTION: character resumes walking
• CAMERA: comes to rest
• LIGHT: warm holds
• EFFECT: speed ramp back to normal
• @REFS: @Image1, @Image2

STYLE: fashion editorial cinematography, natural golden hour, 35mm lens
IDENTITY LOCK: Face from @Image1 identical. Outfit from @Image2 identical — same silhouette, colors, texture
CONSTRAINTS: smooth motion, stable framing, no identity drift
```

This lets Seedance lock face and wardrobe independently. Useful when you have multiple outfits planned for the same character.
