---
name: seedance-prompt-builder
description: Writes paste-ready Seedance 2.0 video prompts from a creative brief. Use whenever the user wants to generate a Seedance prompt, plan a shot, build a product ad, create a brand film, animate a scene, or mentions Seedance, Higgsfield, ByteDance video, or AI video generation. Also trigger when the user describes a visual sequence, ad concept, character action, product demo, or any video they want turned into a generation-ready prompt — even without saying "Seedance." Trigger phrases include "write a video prompt", "Seedance prompt", "make a video of", "animate this", "product ad with AI video", "turn this product photo into a video", "shot list for Seedance", or any brief that needs to become a video generation prompt.
---

# Seedance 2.0 Prompt Builder

Write paste-ready prompts for ByteDance's Seedance 2.0 video model (as accessed via Higgsfield, Dreamina, CapCut, Arcads, or the official API).

## What goes into Seedance — and what doesn't

Only the prompt text and any uploaded references (@Image1, @Video1, @Audio1) go into Seedance. Do NOT generate effects inventories, density maps, energy arcs, or director's breakdowns unless the user explicitly asks for planning notes. Rourke Heath's original skill generated four planning sections — only the shot timeline was actually usable. This skill outputs a single paste-ready prompt by default.

## Workflow

1. Read the user's brief.
2. If the brief is too vague to build a full prompt (e.g. "make something cool"), ask ONE focused clarifying question. Otherwise proceed.
3. If the brief involves a specific use case, load the matching reference file:
   - **Product ads / UGC / ecommerce** → read `references/product-ads.md`
   - **Multi-shot sequences (>6s with scene changes)** → read `references/multi-shot.md`
   - **Multiple uploaded images/videos/audio** → read `references/references-syntax.md`
   - **Character consistency across shots** → read `references/characters.md`
   - **Complex camera choreography** → read `references/camera-moves.md`
4. Build the prompt using the 6-step formula below.
5. Output in the format specified under "Output format."

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

## The @ reference system (quick version)

When the user uploads files, Seedance auto-tags them `@Image1`, `@Image2`, `@Video1`, `@Audio1`, etc. You must reference each tag in the prompt AND assign it a specific role. Max: 9 images + 3 videos (≤15s each) + 3 audio (≤15s each) = 12 references total.

**Assigning roles — quote these exact patterns:**
- `Use @Image1 as the first frame.`
- `Reference @Image2 for outfit and product details only.`
- `Reference @Video1 for camera movement and pacing.`
- `@Audio1 as background music.`

**"Use" vs "Reference":** "Use as first frame" pins the frame exactly. "Reference" borrows the visual idea without forcing the frame.

For multi-reference prompts or character locking, read `references/references-syntax.md` and `references/characters.md`.

## Output format

Always structure the output like this:

```
# Seedance 2.0 Prompt

**Target duration:** [X] seconds
**References to upload:** [list any @Image/@Video/@Audio the user needs to upload, or "text-only"]

## Prompt (copy this into Seedance)

```
[The 60–100 word paste-ready prompt, in plain prose — no markdown inside.
Include the 6 formula elements naturally. Add @references inline where they apply.]
```

**Duration setting in Higgsfield:** [X seconds]
**Aspect ratio:** [16:9 / 9:16 / 1:1 — match brief or default to 16:9]
```

If the user asked for multi-shot, structure the "Prompt" block as a timed shot list (see `references/multi-shot.md`).

Only add a "Director's notes" section at the bottom if the user explicitly asks for planning, effects breakdown, or a shot-by-shot inventory. Default output is prompt-only.

## Constraints: the reliable positive-constraint tail

Append one concise constraint clause at the end of every prompt. Use this as the base template and adapt:

> `smooth stable framing, natural motion, consistent character identity, 4K detail, photographic realism, no temporal flicker, no bent limbs, no warping.`

Pare this down for stylized/animated prompts. For anime or illustrated styles, replace "photographic realism" with the appropriate anchor.

## Duration calibration

- **5–7 seconds:** 1 shot, 1 action, 1 camera move. ~50–70 word prompt.
- **8–10 seconds:** 1–2 shots. ~70–90 words.
- **11–15 seconds:** 2–4 shots, timestamped. ~90–150 words. Use multi-shot syntax.
- **Past 15s:** Seedance generates per-shot up to 15s. For longer videos, generate multiple clips and stitch.

Default to 10 seconds if the user doesn't specify.

## Clarifying questions — only when genuinely stuck

If the brief is workable, don't interrogate. Only ask ONE question if a critical element is missing. Priority of what to ask:

1. If no duration given: assume 10s and note the assumption.
2. If no aspect ratio given: assume 16:9 unless the context obviously points elsewhere (a TikTok UGC brief → 9:16).
3. If no lighting given: make a choice based on mood and state it in the prompt.
4. Only ask if the subject itself is unclear: "Is this a product demo or a person-led ad?"

## Short end-to-end example

**User:** "Quick 8-second UGC ad for a protein bar. Young woman eating it in a kitchen."

**Assistant output:**

```
# Seedance 2.0 Prompt

**Target duration:** 8 seconds
**References to upload:** @Image1 (product photo of the protein bar). If you want a specific creator likeness, you'll need a stylized character sheet — real face photos are blocked.

## Prompt (copy this into Seedance)

A woman in her late twenties in a bright modern kitchen, morning light pouring through a north-facing window, unwraps a protein bar referenced from @Image1 and takes a single slow bite, her expression shifting from curious to genuinely pleased. Camera: handheld medium shot, subtle natural movement, no cuts. Style: iPhone UGC aesthetic, soft natural daylight, warm skin tones, lightly imperfect framing. Keep the product wrapper from @Image1 clean, legible, and identical across the shot. Smooth motion, stable framing, natural skin tones, photographic realism, no warping, no identity drift.

**Duration setting in Higgsfield:** 8 seconds
**Aspect ratio:** 9:16 (UGC default)
```

This example shows the full pattern: subject specific, action one-verb, environment plus lighting, one camera move, style anchor, @ reference with explicit role, positive-constraint tail.
