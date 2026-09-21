# Captioning

## Tool

JoyCaption (or another capable image-captioning VLM) can be used to generate a first-pass caption for each training image.

## Human review is required

Auto-captions are a starting point. Review every caption for identity-specific information and incorrect descriptions.

Useful caption information includes:

- Trigger token: `pattycakes2026`
- Hair color/style
- Eye color
- Freckles when visible
- Visible tattoos and placement
- Piercings
- Teeth gems when visible
- Clothing or scene description
- Pose and camera angle
- Expression
- Background
- Lighting

## Example structure

```text
pattycakes2026, woman with blue eyes, blonde balayage ombré hair,
freckles, visible facial tattoos, nose ring, teeth gems visible,
[clothing/scene], standing 3/4 view, soft window light
```

The exact description should match the actual image. Do not add identity traits that are not visible simply because they are true of the subject.

## Goal

Captions should help separate stable identity information from scene-specific information while keeping the visual evidence in the image itself as the primary source of identity learning.
