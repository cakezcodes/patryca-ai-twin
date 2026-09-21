# Training

## Starting configuration

```yaml
trigger: pattycakes2026
dataset_images: 30-50
resolution: 1024
rank: 64
learning_rate: 0.0002
batch_size: 1-2
steps: 1500
checkpoint_interval: 250
```

## Workflow

1. Prepare the final image/caption pairs.
2. Verify filenames and caption matching.
3. Start the training run.
4. Save intermediate checkpoints.
5. Generate the same validation prompts against each checkpoint.
6. Score likeness and generalization.
7. Select the strongest checkpoint.
8. Record the winning checkpoint and exact settings in the experiment log.

## Evaluation

Do not select a checkpoint based on one favorite image. Test multiple categories:

- Close portrait
- 3/4 portrait
- Full body
- Different background
- Different lighting
- Different pose
- Tattoo visibility
- Hair consistency
- Skin/detail quality

The research plan recommends intermediate saves specifically so overtraining can be detected and an earlier checkpoint selected when appropriate. fileciteturn1file0L453-L472

## Training risks

### Undertraining
Symptoms: weak resemblance, missing identity traits, generic base-model face.

Potential experiments: more steps, stronger dataset coverage, or higher rank.

### Overtraining
Symptoms: outputs become too similar to training images, artifacts increase, generalization drops.

Potential experiments: choose an earlier checkpoint, reduce learning rate, or improve dataset variety.

### Identity drift
If identity quality drops when adding other LoRAs, remove unnecessary LoRAs before changing the Person LoRA itself.
