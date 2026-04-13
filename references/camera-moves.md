# Camera Moves & Motion Control for Seedance 2.0

Load this when the user needs complex camera choreography or you're unsure which move fits the brief.

## Contents
- The 8 primary camera movements
- When to use each
- Pacing words that replace technical specs
- How to handle compound camera motion
- Motion keywords that break Seedance

## The 8 primary camera movements

Use EXACTLY ONE per shot. Stacking multiple in a single shot causes jitter.

| Move | Keyword phrasing | When to use |
|---|---|---|
| **Push-in / Dolly In** | `slow dolly-in, 1–2 feet` or `push in on [subject]` | Emotional focus, building tension, hero reveal of product |
| **Pull-out / Dolly Out** | `slow dolly-out revealing [wider context]` | Environment reveal, scale reveal, "god shot" establishment |
| **Pan (Lateral)** | `slow pan right revealing [element]` | Scanning an environment, following a horizontal action |
| **Tracking / Follow** | `tracking shot alongside [subject]` | Action scenes, walking/running, parallel to subject |
| **Orbit / Arc** | `slow orbit around [subject]` or `360 orbit` | Product showcases, portraits, hero beats |
| **Aerial / Drone** | `aerial shot from above, slow descent` | Landscapes, scale reveals, opening shots |
| **Handheld** | `handheld medium shot, subtle natural shake` | UGC, documentary, raw/real feel |
| **Fixed / Locked-off** | `static locked-off camera` or `no camera movement` | Dialogue beats, clean product shots, when the action is the story |

## Pacing words (use these — they replace technical jargon)

Seedance responds to natural pacing language, not photography specs. Use:

- **Slow** — most common, safest default
- **Smooth** — prevents jitter
- **Gentle** — subtle, unforced
- **Gradual** — for push-ins and pull-outs
- **Stable** — for framing, locked-down feel
- **Continuous** — for single-take feel

Do NOT use: `24fps`, `aperture f/1.8`, `ISO 400`, `shutter 1/60`. Seedance doesn't parse photography parameters. It treats them as noise.

## Compound camera motion — split into shots

If the creative calls for "camera pushes in WHILE orbiting WHILE tilting up," that's three moves. Seedance will produce chaos. Split it into three consecutive shots in the SHOT format defined in SKILL.md — each shot gets one CAMERA bullet. For example: shot 1 dolly-in, shot 2 orbit, shot 3 tilt-up.

## Motion keywords that break Seedance

### The single most dangerous word: `fast` (unqualified)
Combining `fast camera` + `fast cuts` + `busy scene` = total quality collapse. Pick ONE thing to be fast, describe it physically, and keep the rest calm.

### Stacking motion verbs
`she walks, turns, jumps, waves, and smiles` → confused output. Rule: **one verb per shot.** Break complex actions into timed shots.

### Vague adjectives
`amazing`, `beautiful`, `epic`, `stunning`, `breathtaking` → no practical guidance for the model. Replace with specifics: `warm golden hour backlight` beats `beautiful lighting.`

### "Lots of movement"
Triggers jitter. Instead describe the single specific motion: `wind blowing leaves across the path from camera-right to camera-left.`

## Motion keywords that work

- `quickly, slowly, dramatically, vigorously, gently, powerfully` — qualified speed
- `streaking into motion blur` — for speed with intentional aesthetic
- `tires screeching, dust kicking up` — physics-specific descriptions
- `smooth stabilized motion` — locked, polished feel
- `micro-movements, subtle shake` — UGC-style natural realism

## Lighting is stronger than any camera move

Remember: lighting changes have a bigger impact on output quality than any camera instruction. If the shot looks flat or generic, fix the lighting description before adjusting the camera.

See also: the Rule 2 section in SKILL.md for specific lighting vocabulary.
