# Identity Architecture

## Primary identity

The project uses **`patryca`** as the sole Person LoRA trigger word.

The Person LoRA is intended to capture the creator's identity characteristics: face, body proportions, hair, tattoos, piercings, teeth gems, and other stable personal features represented in the training dataset.

## Other people and visual references

Other people do **not** require a separate Person LoRA merely because they appear in a generated scene.

For visual information about another person, use reference-image conditioning (such as IP-Adapter/reference conditioning) at generation time when the workflow supports it. This keeps the project centered on one trained identity model rather than accumulating multiple personal LoRAs.

### Zay / male reference material

If reference images of Zay are used for a generation, they are generation-time reference assets only. They are **not** a `zaybae` LoRA and `zaybae` is not a model trigger word.

Reference assets should remain private and outside the Git repository.

## Architecture

```text
Base Model
    |
    +--> Person LoRA: patryca
    |
    +--> Reference conditioning (when needed)
           +--> clothing/items
           +--> room/environment
           +--> other visual references
           +--> another person's visual features
```

## Rule

**One trained personal identity: `patryca`.**

Reference images can supply changing visual context without creating a new personal LoRA for every person, object, outfit, or environment.
