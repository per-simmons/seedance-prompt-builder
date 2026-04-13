# Product Ad Patterns for Seedance 2.0

Load this when the user is making an ad: UGC, ecommerce, DTC, brand film, product demo, Meta/TikTok ad, or "I want an ad for X."

## Contents
- Product-ad-specific rules
- The four proven ad formats
- Handling the "no real faces" constraint
- Product consistency techniques
- UGC voice and styling
- Full worked examples

## Product-ad-specific rules

1. **Always upload the product photo as @Image1** and assign it the role: `Reference @Image1 for product shape, label text, and material. Keep the product identical across the shot.` Product drift is the #1 failure mode in AI-generated ads.

2. **720p is fine for social.** Seedance 2.0 outputs at 720p; that's enough for phone-first platforms (TikTok, Reels, Stories, Meta ads). Don't over-engineer resolution.

3. **Aspect ratio defaults by platform:**
   - TikTok / Reels / Stories / Shorts → 9:16
   - Meta / Instagram feed → 1:1 or 4:5
   - YouTube pre-roll / landing page → 16:9
   - Ask if unclear.

4. **Dialogue in UGC works** but keep it short — one line of natural dialogue per 5 seconds max. Seedance generates native audio; the TikTok-native delivery is part of why it converts.

5. **Lighting mimics the platform:**
   - UGC: `soft natural daylight through a window, slightly imperfect handheld framing`
   - Polished commercial: `three-point studio lighting, soft key from camera-left, warm rim light`
   - Cinematic brand film: `golden hour backlight, volumetric god rays, soft shadow detail`

## The four proven ad formats

### Format 1 — Hand-demo UGC (highest conversion for physical products)
First-person or over-the-shoulder; hands interact with the product. Avoids the face-block problem entirely.

Template:
```
Close-up of a pair of hands [interaction with product from @Image1] on a [surface] in [lighting]. [Product] from @Image1 stays identical, label legible and facing camera on the final beat. [Single camera move]. Style: iPhone UGC, slightly imperfect framing, natural daylight. Smooth motion, stable framing, product identity locked, no warping.
```

### Format 2 — Character testimonial (works if you have a stylized character sheet)
Requires a character-sheet reference (not a real face photo) to avoid the upload block.

Template:
```
Medium shot of the character from @Image1 in [environment, lighting]. They hold up the product referenced from @Image2, look at camera, and deliver a single natural line: "[dialogue]." [Single camera move]. Style: [anchor]. Keep character face and outfit identical to @Image1, keep product from @Image2 identical. Smooth motion, natural skin tones, no identity drift.
```

### Format 3 — Product hero shot / cinematic macro (no human needed)
Pure product cinematography. Simplest to execute. No face restrictions. No UGC tradeoffs.

Template:
```
Extreme macro on the [product] from @Image1, [specific detail/texture moment — e.g., condensation beading on the bottle, fibers of fabric catching light]. [Lighting — be specific]. Camera: slow dolly-in, 1–2 feet. Style: commercial product cinematography, shallow depth of field, [color treatment]. Product from @Image1 identical, label sharp and readable. Smooth focus, stable framing, no warping.
```

### Format 4 — Transformation / before-after
Leverages Seedance's multi-shot strength. Great for skincare, cleaning products, software UIs.

See `references/multi-shot.md` for timestamp syntax, then apply this template:
```
Shot 1 (0–4s): [before state — clear, visible, lit to show the problem]. Shot 2 (4–7s): The product from @Image1 enters frame, [application action]. Shot 3 (7–10s): [after state — clear, visible, lit to show the improvement]. Style: [anchor]. Product from @Image1 identical throughout. Smooth motion, natural transitions, no flicker between shots.
```

## Handling the "no real faces" constraint creatively

Seedance blocks identifiable real-face photo uploads at the upload stage. This is not negotiable. But the workarounds are many:

| Approach | How |
|---|---|
| **Hands-only** | First-person or over-the-shoulder hands-on-product. Format 1. |
| **Obscured face** | Product covers part of the face; hat brim shadows; hair across the face; sunglasses. |
| **Back of head / profile** | Prompt-specify the framing; avoid real-face references altogether. |
| **Silhouette** | Backlit silhouette against a window or sky. |
| **Stylized character sheet** | Generate a non-photorealistic character in Nano Banana / Midjourney / Flux first, then use that as @Image1. Seedance's scanner doesn't block stylized characters. |
| **Text-only human description** | Skip the image reference entirely for the person; describe them in prose. The scanner only fires on uploaded images. |
| **Product-only** | Format 3. No humans involved. |

## Product consistency techniques

Product identity drift across shots is the most common failure. These techniques fix it:

1. **Upload at 2K+ resolution.** Low-res product references = drift.
2. **Explicit role assignment.** `Reference @Image1 for product shape, label text, colors, and material. Product stays identical in every shot.`
3. **Repeat the product identity lock in the constraint tail.** `Product from @Image1 identical, label sharp and legible, no warping.`
4. **For multi-shot ads**, reference `@Image1` in each individual shot description, not just once at the top.
5. **Simpler products consistify better.** A bottle with one logo holds shape better than a multi-panel box with tiny text.
6. **If the label has text**, the text WILL wobble slightly. You can't fully prevent this. Consider: hero the product silhouette and use post-production to inpaint a clean label on the final frame if needed.

## UGC voice and styling — what actually converts

From Arcads and creator-tested patterns:

- **Framing:** handheld, slightly off-center, phone-level height (not eye-level)
- **Lighting:** soft natural daylight, ideally from a window behind or beside the camera
- **Delivery:** "casual friend telling you about a product" — NOT "spokesperson reads a script"
- **Dialogue rhythm:** one natural beat per 5 seconds. Include a discovery moment ("wait"), a qualifier ("honestly"), or a reaction ("oh")
- **Resolution:** 720p is a feature, not a bug — adds organic texture
- **Background:** messy-but-lived-in. A perfectly clean kitchen screams "ad." A kitchen with one mug on the counter and a pot on the stove screams "real person."

## Full worked examples

### Example: Glass serum bottle — macro hero shot (Format 3)

```
Extreme macro on the glass serum bottle from @Image1, a single amber droplet beading at the dropper tip and slowly releasing, catching the light as it falls. Soft north-window daylight from camera-left, warm amber refraction through the glass, shallow depth of field on the droplet. Camera: slow dolly-in, 1 foot over 6 seconds, no cuts. Style: commercial beauty cinematography, 35mm film texture, muted warm palette. Product from @Image1 identical, label sharp and legible throughout. Smooth focus, stable framing, natural liquid motion, no warping, no flicker.
```

### Example: Protein bar UGC (Format 1, hands + over-shoulder)

```
Over-the-shoulder shot of a pair of hands unwrapping the protein bar from @Image1 on a bright modern kitchen counter, morning light through a large north-facing window. The hands peel the wrapper back halfway, then break off a piece and bring it up out of frame. The bar's label from @Image1 stays visible and legible throughout. Camera: handheld medium shot, subtle natural movement, no cuts. Style: iPhone UGC, warm natural daylight, lightly imperfect framing. Product from @Image1 identical, wrapper clean and readable. Smooth motion, stable framing, no warping, no identity drift.
```

### Example: Stanley cup transformation (Format 4, multi-shot)

```
Shot 1 (0–3s): The Stanley tumbler from @Image1 sits on a pristine modern desk, soft daylight from a window, camera static wide. Shot 2 (3–7s): A hand enters frame and picks it up, lifting it toward the camera as the environment warps through a seamless transition into a mountain trail at golden hour — same Stanley tumbler from @Image1 still in hand, steam now rising from the lid. Shot 3 (7–10s): The Stanley from @Image1 sits on a rock, mountain range behind it, golden hour backlight, camera slow push-in. Style: cinematic lifestyle commercial, warm color grade, shallow depth of field. Product from @Image1 identical throughout — same color, same logo, same shape. Smooth transitions, stable framing, consistent product identity, no warping, no flicker.
```
