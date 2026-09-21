# Experiments

Every meaningful training change gets an experiment entry.

## Record

- Experiment ID
- Date
- Base model/version
- Dataset version and image count
- Trigger token
- Rank
- Learning rate
- Resolution
- Batch size
- Steps
- Checkpoint interval
- Generation settings
- Reference-conditioning settings
- Validation prompts
- Results
- Winner
- What changed from the previous run

## Why

The point is to make the project reproducible. If a new LoRA is better, we should know **why** it was better instead of relying on memory.
