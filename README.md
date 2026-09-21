# pattycakes-ai

The full project behind my AI avatar: photos, training, experiments, workflows, and generation.

> **Status:** Building v1.0 — Person LoRA + reference conditioning

## What this project is

A version-controlled workspace for building a consistent AI version of me. The core system is intentionally simple:

**One strong Person LoRA** learns stable identity features — face, body proportions, hair, tattoos, piercings, freckles, teeth gems, and other distinctive traits.

**Reference images / IP-Adapter** handle things that change from generation to generation — lingerie, jewelry, rooms, props, and other specific visual references.

**ComfyUI** is the generation layer. Training and generation are kept separate so the project can be tested, versioned, and improved without turning every new item into another LoRA.

## Core architecture

```text
Training photos + captions
          │
          ▼
   Person LoRA training
          │
          ▼
   Identity LoRA (.safetensors)
          │
          ├──────────────┐
          ▼              ▼
       Prompt       Reference image
          │          / IP-Adapter
          └──────┬───────┘
                 ▼
              ComfyUI
                 │
                 ▼
        Generated content
```

## Project rules

1. Identity belongs in the Person LoRA.
2. Do not create separate LoRAs for personal tattoos, hair, body, or ordinary clothing unless an experiment proves there is a real need.
3. Use reference images for specific reusable items and environments.
4. Keep the training dataset small enough to curate carefully: the current target is **30–50 high-quality, varied images**.
5. Save intermediate checkpoints and evaluate them instead of assuming the final checkpoint is best.
6. Keep private photos, reference material, generated media, model weights, and credentials out of Git.
7. Every meaningful training change gets recorded as an experiment.

## Current training target

| Setting | Target |
|---|---|
| Trigger | `pattycakes2026` |
| Dataset | 30–50 curated images |
| Resolution | 1024 where hardware allows |
| LoRA rank | 64 starting point |
| Learning rate | `2e-4` starting point |
| Batch size | 1–2 |
| Training steps | ~1500; evaluate earlier checkpoints |
| Checkpoints | Every 250 steps |
| Generation LoRA weight | Start around 0.7–0.8 and test |
| Style LoRAs | 0–1, only when actually useful |

These are starting values, not promises. The experiment log is the source of truth for what actually works for this dataset/model combination.

## Dataset priorities

The dataset should teach identity rather than memorize a handful of photographs. It should cover:

- Front, 3/4, and profile face angles
- Multiple expressions
- Hair down/up and straight/wavy variations while preserving the real color
- Full-body, medium, and close-up framing
- Body proportions and scale references
- Every distinctive tattoo from useful angles
- Freckles and other facial details
- Piercings and teeth gems where visible
- Varied lighting and backgrounds
- Enough variation to generalize beyond the training photos

The research/build plan specifically emphasizes that stable physical identity traits belong in the Person LoRA and that clothing, pose, backgrounds, and other transient elements should generally be handled through prompts or references. fileciteturn1file0L14-L24 fileciteturn1file0L71-L74

## Repository layout

```text
pattycakes-ai/
├── README.md
├── .gitignore
├── docs/
│   ├── PLAYBOOK-V2.md
│   ├── ARCHITECTURE.md
│   ├── DATASET.md
│   ├── TRAINING.md
│   ├── GENERATION.md
│   ├── CAPTIONING.md
│   ├── PRIVACY.md
│   └── CHANGELOG.md
├── configs/
│   ├── person-lora.md
│   └── generation.md
├── prompts/
│   ├── README.md
│   └── scene-library.md
├── experiments/
│   ├── README.md
│   └── 001-baseline.md
├── workflows/
│   └── README.md
├── dataset/
│   └── README.md
└── reference-photos/
    └── README.md
```

The directories for private assets are documented but intentionally do **not** contain personal media in this repository.

## Tools

- Person LoRA training: FluxGym / RunPod
- Generation: ComfyUI
- Captioning: JoyCaption or comparable VLM captioner
- Reference conditioning: IP-Adapter or equivalent reference workflow
- Upscaling: 4x-UltraSharp / comparable upscaler
- Optional final correction: inpainting / face-detail tools

## Versioning

The repo tracks the system, not the private media.

Training runs should record:

- Base model and exact model version
- Dataset version/count
- Trigger token
- Rank
- Learning rate
- Resolution
- Batch size
- Total steps
- Checkpoint results
- Prompt/reference conditions used for evaluation
- What changed from the previous experiment
- Which checkpoint won and why

## Privacy

This is a **private repository**. Personal photos, partner/reference material, generated adult content, model weights, and credentials stay outside Git unless explicitly reviewed for safe publication.

See [`docs/PRIVACY.md`](docs/PRIVACY.md).

## License

No open-source license is currently applied. This repository is private and intended for personal use.
