# Product Ad Patterns for Seedance 2.0

Load when the user is making an ad: UGC, ecommerce, DTC, brand film, product demo, Meta/TikTok ad. Examples use the strict SHOT N bullet format defined in SKILL.md.

## Contents
- Product-ad-specific rules
- The four proven formats
- Handling the face-upload restriction
- Product consistency techniques
- UGC voice
- Full worked examples

## Product-ad-specific rules

1. Upload the product photo as `@Image1`. Assign the role in the `@REFS` bullet of every shot where it appears: `@Image1 for shape + label`.
2. 720p is fine for phone-first platforms (TikTok, Reels, Stories, Meta ads).
3. Aspect ratio defaults: TikTok/Reels/Stories → 9:16 · Meta/IG feed → 1:1 or 4:5 · YouTube/landing → 16:9.
4. UGC dialogue: one natural beat per 5 seconds, include a discovery ("wait"), qualifier ("honestly"), or reaction ("oh").
5. Lighting signatures: UGC = `soft natural window daylight, handheld framing` · Commercial = `three-point studio, soft key camera-left, warm rim` · Brand film = `golden hour backlight, volumetric god rays`.
6. Every ad has one SIGNATURE beat — the visual moment that makes it memorable.

## The four proven formats

Each format is a shot-count recipe. Fill in the ACTION/CAMERA/LIGHT/EFFECT/@REFS bullets using the brief.

### Format 1 — Hand-demo UGC (first-person / over-the-shoulder, no face problem)
Shape (10s, 5 shots):
1. **Rest** — hands near product, low density
2. **Approach** — hands pick up product, 6-inch dolly-in
3. **Interaction (SIGNATURE)** — the specific tactile moment (peel / pour / swipe), stacked rack focus + speed ramp
4. **Result** — speed ramps back up, hands show the outcome
5. **Resolve** — hands set product back, label toward camera, framing stabilizes

### Format 2 — Character testimonial (requires stylized `@Image1` character sheet + `@Image2` product)
Shape (10s, 5 shots):
1. **Hold** — character holds product at chest height
2. **Present** — character brings product closer, 1-foot dolly-in
3. **Delivery (SIGNATURE)** — single natural dialogue line, rack focus from product to face
4. **React** — expression settles into genuine reaction
5. **Resolve** — character lowers product, natural rest pose

### Format 3 — Product hero / cinematic macro (no human)
Shape (10s, 5 shots):
1. **Rest** — product still on surface, locked macro, low density
2. **Motion begins** — subtle initiation (lid opens / droplet forms / element enters), slow dolly-in 6 inches
3. **Hero moment (SIGNATURE)** — the specific visual payoff (droplet falls / LED pulses / cap snaps), stacked rack focus + speed ramp to ~30–40%
4. **Settle** — speed ramps to normal, product finds final pose, dolly-in continues to 1 foot
5. **Resolve** — motion ceases, hero frame holds in stillness

### Format 4 — Transformation / before-after
Shape (12s, 6 shots):
1. **Before** — problem state visible, flat lighting, wide static
2. **Entry** — product enters frame in hand or on surface, warmer key light rises
3. **Application (SIGNATURE)** — the specific use moment (swipe/spray/tap), rack focus + speed ramp to ~30%
4. **Begins** — speed back to normal, visible change begins
5. **After** — wide re-establish showing transformed state, same location as shot 1
6. **Resolve** — product hero-framed, label clean, final calm beat

## Handling the face-upload restriction

Identifiable real faces are blocked at upload. Workarounds:
- **Hands-only** (Format 1) — no face needed
- **Obscured face** — product covers face / hat brim / hair / sunglasses
- **Back of head / profile / silhouette** — specify in ACTION bullet
- **Stylized character sheet** — generate in Nano Banana / Flux / Midjourney, use as `@Image1`
- **Product-only** (Format 3) — no humans
- **Text-only human description** — skip the image ref, describe in ACTION bullet

## Product consistency techniques

1. Upload at 2K+ resolution.
2. Include `@Image1 for shape + label` in the `@REFS` bullet of every shot where the product appears.
3. `IDENTITY LOCK: Product from @Image1 identical throughout — same shape, label, colors.` at the end.
4. Simpler products consistify better (single logo beats multi-panel box with tiny text).
5. Label text wobbles slightly — can't fully prevent. For hero label shots, inpaint in post.

## UGC voice — what converts

- Framing: handheld, slightly off-center, phone-level height
- Lighting: soft natural daylight from window behind/beside camera
- Delivery: "casual friend," not spokesperson
- Background: messy-but-lived-in beats pristine

## Full worked examples

### Example: Glass serum bottle — macro hero (Format 3, 10s)

```
SHOT 1 (0–2s) — Rest
• ACTION: serum bottle sits still, dropper cap closed, droplet not yet forming
• CAMERA: locked-off close, 35mm macro lens feel
• LIGHT: soft north-window daylight from camera-left, warm amber refraction through glass
• EFFECT: none, low density
• @REFS: @Image1 for bottle shape + label

SHOT 2 (2–4s) — Dropper Lifts
• ACTION: dropper cap begins to lift slowly, thin golden thread of serum clinging underneath
• CAMERA: slow dolly-in, 6 inches
• LIGHT: unchanged
• EFFECT: none
• @REFS: @Image1 still visible

SHOT 3 (4–6s) — Droplet Falls (SIGNATURE)
• ACTION: single amber droplet beads at dropper tip and falls
• CAMERA: continues slow dolly-in
• LIGHT: droplet catches light mid-fall
• EFFECT: stacked — shallow rack focus shift from bottle to droplet + speed ramp (deceleration) to ~25% speed
• @REFS: @Image1 still visible

SHOT 4 (6–8s) — Lands
• ACTION: droplet lands on surface and spreads slowly
• CAMERA: continues slow dolly-in, now 1 foot closer
• LIGHT: unchanged
• EFFECT: speed ramp (acceleration) back to normal
• @REFS: @Image1 bottle in frame

SHOT 5 (8–10s) — Resolve
• ACTION: dropper back over bottle, serum bead rests on surface
• CAMERA: comes to rest
• LIGHT: warm sidelight holds
• EFFECT: none
• @REFS: @Image1 label legible and sharp

STYLE: commercial beauty cinematography, 35mm film texture, muted warm palette, shallow depth of field with soft bokeh
IDENTITY LOCK: Product from @Image1 identical throughout — same shape, label, glass clarity
CONSTRAINTS: smooth focus, stable framing, natural liquid motion, no warping, no flicker
```

### Example: Wireless earbuds case — Apple-grade hero (Format 3, 10s)

```
SHOT 1 (0–2s) — Rest
• ACTION: earbuds case sits closed and still on matte black marble
• CAMERA: locked-off macro, 35mm lens feel
• LIGHT: cool white three-point key from camera-right, warm rim along case edge, shallow depth of field
• EFFECT: none, pure stillness
• @REFS: @Image1 for case shape, proportions, glossy white finish

SHOT 2 (2–4s) — Lid Opens
• ACTION: lid of case begins to open slowly, revealing inside edge
• CAMERA: slow dolly-in, 6 inches
• LIGHT: unchanged
• EFFECT: none
• @REFS: @Image1 for case identity

SHOT 3 (4–6s) — Earbuds Rise (SIGNATURE)
• ACTION: both earbuds rise slightly as if magnetically lifted; green LED indicator pulses once
• CAMERA: continues slow dolly-in
• LIGHT: LED soft bloom briefly lifts the midtones
• EFFECT: stacked — shallow rack focus shift from lid to LED + speed ramp (deceleration) to ~40% speed during pulse
• @REFS: @Image1 for case + earbud identity

SHOT 4 (6–8s) — Settle
• ACTION: earbuds settle into raised position, lid fully open, LED steady
• CAMERA: continues slow dolly-in, now ~1 foot closer
• LIGHT: unchanged
• EFFECT: speed ramp (acceleration) back to normal
• @REFS: @Image1

SHOT 5 (8–10s) — Resolve
• ACTION: everything holds, case fully revealed in hero framing, glossy white finish catches rim light
• CAMERA: comes to rest
• LIGHT: cool key + warm rim hold
• EFFECT: none
• @REFS: @Image1 proportions and finish identical

STYLE: commercial product cinematography, Apple-grade minimalism, muted cool palette with warm rim accents, 35mm film texture, shallow depth of field
IDENTITY LOCK: Product from @Image1 identical throughout — same shape, proportions, glossy white finish
CONSTRAINTS: smooth focus, stable framing, no warping, no flicker, no identity drift
```

### Example: Stanley tumbler transformation (Format 4, 12s)

```
SHOT 1 (0–2s) — Before
• ACTION: Stanley tumbler sits still on pristine modern desk, lid closed
• CAMERA: wide locked-off
• LIGHT: flat daylight from left window
• EFFECT: none, low density
• @REFS: @Image1 for tumbler shape + color + logo

SHOT 2 (2–3.5s) — Hand Enters
• ACTION: hand enters frame from right, reaches toward the tumbler
• CAMERA: cut to medium close
• LIGHT: unchanged
• EFFECT: none
• @REFS: @Image1

SHOT 3 (3.5–5s) — Lift
• ACTION: hand lifts the tumbler off desk toward camera
• CAMERA: dolly-in, 6 inches
• LIGHT: unchanged
• EFFECT: none
• @REFS: @Image1

SHOT 4 (5–7s) — Environment Warp (SIGNATURE)
• ACTION: as the tumbler moves through frame, the desk dissolves into a mountain trail at golden hour around it
• CAMERA: continues dolly-in
• LIGHT: daylight transitions into warm golden backlight
• EFFECT: stacked — environment dissolve + speed ramp (deceleration) to ~50% speed through the warp
• @REFS: @Image1 identical through the warp

SHOT 5 (7–8.5s) — Settle
• ACTION: hand places tumbler on a granite rock, steam rises from the lid
• CAMERA: locked medium
• LIGHT: warm golden hour backlight now fully established
• EFFECT: speed ramp (acceleration) back to normal
• @REFS: @Image1

SHOT 6 (8.5–10.5s) — Hero
• ACTION: tumbler sits hero-framed on rock, mountain range behind
• CAMERA: slow dolly-in to hero the lid
• LIGHT: warm golden hour holds
• EFFECT: none, medium density
• @REFS: @Image1

SHOT 7 (10.5–12s) — Resolve
• ACTION: motion ceases, tumbler in final hero pose
• CAMERA: comes to rest
• LIGHT: warm light holds
• EFFECT: none
• @REFS: @Image1 identical — same color, logo, shape

STYLE: cinematic lifestyle commercial, warm color grade, shallow depth of field
IDENTITY LOCK: Product from @Image1 identical throughout — same color, same logo, same shape
CONSTRAINTS: smooth environmental transition, stable framing on the after state, consistent product identity, no warping, no flicker
```
