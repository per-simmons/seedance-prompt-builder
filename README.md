# Seedance Prompt Builder

A Claude Agent Skill that turns plain-English briefs into paste-ready prompts for **Seedance 2.0** (ByteDance's AI video model, accessed via Higgsfield, Dreamina, CapCut, Arcads, or the API).

Talk to Claude like a director. It hands you back a prompt you drop straight into Higgsfield.

## What makes this different

Built on research from [the Seedance 2.0 launch videos](#) and verified against the official prompting docs:

- **Paste-ready output by default** — no planning-tool overhead. You get the prompt, you paste it.
- **Grounded in real Seedance rules** — one camera instruction per shot, lighting as the #1 quality driver, `"fast"` as the most dangerous keyword, the `@Image1` reference system, the real-face upload restriction.
- **Product ad focus** — four proven ad formats (hands-only UGC, character testimonial, product hero macro, before-after transformation) with templates for each.
- **Progressive disclosure** — the main `SKILL.md` stays tight (~150 lines). Five reference files load only when the conversation needs them:
  - `product-ads.md` — ad formats, face workarounds, UGC voice
  - `camera-moves.md` — the 8 camera types, compound-motion handling
  - `multi-shot.md` — timestamp syntax, transitions, per-shot identity locking
  - `references-syntax.md` — the `@Image1` / `@Video1` / `@Audio1` role assignment system
  - `characters.md` — character sheets, face restrictions, drift fixes

## Install

1. Download [`seedance-prompt-builder.skill`](./seedance-prompt-builder.skill)
2. In **Claude Desktop** (claude.ai): **Settings → Customize → Skills → + → Upload a skill** → pick the file.
3. That's it. The skill triggers automatically whenever you talk about making a Seedance video, product ad, or any video generation prompt.

## Example usage

**You:** "Make me a 10-second ad for a protein bar. Young woman eating it in a bright kitchen."

**Claude** (via the skill) gives you a structured output with:
- The paste-ready prompt (60–100 words, following the 6-step formula)
- A note on which files to upload as `@Image1`, etc.
- Duration and aspect-ratio settings for Higgsfield

Copy the prompt block, paste into Higgsfield, upload any referenced images, hit generate.

## The 6-step formula (core of every prompt)

```
[Subject], [Action], in [Environment], camera [Camera], style [Style], avoid [Constraints]
```

- **Subject** — specific, not generic
- **Action** — ONE verb per shot, quantified intensity
- **Environment** — location AND lighting (lighting is the highest-impact element)
- **Camera** — exactly ONE primary move per shot
- **Style** — one strong visual anchor, not stacked adjectives
- **Constraints** — positive-phrased guardrails (Seedance has no true negative prompts)

## Critical Seedance rules the skill enforces

1. **One camera instruction per shot** — multiple moves cause jitter
2. **Lighting outranks everything else** — one line about lighting beats ten style adjectives
3. **`fast` (unqualified) is the single most dangerous keyword** — causes warp, flicker, identity drift
4. **No true negative prompts** — use positive constraint language instead (`ultra-realistic, photographic` not `no 3D, no cartoon`)
5. **Identifiable real faces blocked at upload** — use stylized character sheets (Nano Banana, Flux, Midjourney)
6. **One shot, one verb** — stacking motion verbs in a single shot confuses the model
7. **Reference videos should be short** — trim to the key segment

## Credit

Inspired by Rourke Heath's original [video prompt builder](https://www.youtube.com/watch?v=tYJQusOS2jI) but rebuilt from scratch:
- Dropped the four planning sections (effects inventory, density map, energy arc) — only the shot timeline actually goes into Seedance
- Grounded in the official [Seedance 2.0 prompt guide](https://help.apiyi.com/en/seedance-2-0-prompt-guide-video-generation-camera-style-tips-en.html) and Higgsfield's docs
- Added the `@Image1` reference syntax system (absent from the original)
- Added product-ad-specific templates
- Follows [Claude Agent Skills best practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices) — progressive disclosure, third-person description, one-level-deep references

## License

MIT — do whatever you want with it.
