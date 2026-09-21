# AI Me — LoRA Playbook v2

## Goal

Build one strong Person LoRA that learns the stable visual identity of the subject: face, body, tattoos, hair, teeth gems, piercings, freckles, and proportions.

Specific clothing, rooms, jewelry, props, and other transient items are handled at generation time with prompts and reference images rather than creating a separate personal LoRA for every item.

## Trigger

`pattycakes2026`

The trigger was changed from `pattycakes` to a more unique token to reduce possible vocabulary associations.

## Pipeline

1. Photograph a broad identity dataset.
2. Cull to roughly 30–50 strong, varied images.
3. Apply consistent editing only after culling.
4. Auto-caption with JoyCaption or a comparable captioning VLM.
5. Review captions for identity traits, placement, pose, clothing, lighting, and background.
6. Train the Person LoRA.
7. Save intermediate checkpoints.
8. Evaluate checkpoints using consistent test prompts.
9. Select the best identity checkpoint rather than automatically choosing the last one.
10. Generate in ComfyUI with the Person LoRA plus reference conditioning when needed.

## Dataset priorities

### Face

Capture front, 3/4 left, 3/4 right, profiles, tilted angles, looking up/down, neutral and smiling expressions, and close-ups where freckles, piercings, teeth gems, and facial tattoos are clear.

### Hair

Capture the real blonde balayage/ombré gradient in natural light and across straight, wavy/curly, down, ponytail, half-up, and textured arrangements.

### Body

Use a mix of medium and full-body shots, multiple outfits, sitting/standing/turning positions, and some shots with door frames or furniture to provide scale cues.

### Tattoos

Every distinctive tattoo should be represented clearly enough for the model to learn placement. Use close-ups plus wider shots that show how tattoos relate to the body.

### Lighting/background

Vary natural/window light, warm light, ring light, outdoor light, bedroom, bathroom, plain walls, living spaces, and other backgrounds. Avoid allowing one background to dominate the dataset.

## Training starting point

| Setting | Starting value |
|---|---|
| Dataset | 30–50 curated images |
| Resolution | 1024 where hardware allows |
| Rank | 64 |
| Learning rate | 2e-4 |
| Batch size | 1–2 |
| Steps | ~1500 |
| Save interval | 250 steps |
| Evaluation | 500 / 750 / 1000 / 1250 / 1500 |

These are experiment starting points. Actual results should be recorded under `experiments/`.

## Generation architecture

**Base model → Person LoRA → optional style LoRA → reference conditioning → prompt → sampler → correction/upscale → output**

Keep LoRA stacking minimal. The research plan recommends a single Person LoRA as the default and treats reference conditioning as an optional identity aid for difficult cases. fileciteturn1file0L663-L685

## Reference images

Reference images can be maintained for specific lingerie, rooms, jewelry, props, and other visual concepts. They are generation inputs, not training assets, unless an experiment explicitly changes that decision.

## Checkpoint selection

Do not assume the final step is best. Compare checkpoints using the same identity test prompts and score:

- Face likeness
- Body consistency
- Hair consistency
- Tattoo placement
- Skin/detail quality
- Generalization to new backgrounds/poses
- Artifacts or overtraining

The research plan specifically recommends periodic checkpoint saves and evaluation to detect overfitting and choose the strongest likeness. fileciteturn1file0L453-L472

## Important boundary

This document describes the workflow architecture. It does not replace model-specific documentation. Base-model licensing, trainer compatibility, ComfyUI node compatibility, and current tool behavior should be verified before each production run.
