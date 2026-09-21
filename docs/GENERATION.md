# Generation

## Core workflow

```text
Base model
   ↓
Person LoRA
   ↓
Optional style LoRA
   ↓
Reference conditioning / IP-Adapter (when needed)
   ↓
Prompt + sampler
   ↓
Face/detail correction if needed
   ↓
Upscale
   ↓
Save
```

## Prompt structure

```text
[trigger], [subject description], [pose], [clothing/reference],
[tattoos/identity details], [location], [lighting], [expression],
[camera/style details]
```

## Identity-first troubleshooting

**Face is wrong:** test Person LoRA weight first; do not immediately stack another identity LoRA.

**Tattoo is missing:** verify dataset coverage, captioning, prompt/reference conditioning, and checkpoint selection.

**Hair is wrong:** verify that the training dataset consistently represents the real hair color and style.

**Output is too artificial:** test lighting, skin/detail prompting, style weight, and reference strength rather than blindly increasing identity weight.

**Reference item is wrong:** adjust the reference-conditioning workflow and reference image quality.

**Hands/details are wrong:** regenerate or use a targeted correction workflow.

## Validation rule

Keep a small set of repeatable test prompts. Changing the prompt, reference image, and checkpoint all at once makes it impossible to tell what improved the output.
