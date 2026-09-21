# Dataset

This directory documents the dataset structure. **Do not place private training images in GitHub.**

## Suggested private structure

```text
private-dataset/
├── raw/
├── culled/
├── edited/
├── captions/
└── selected/
```

The repository only tracks documentation and non-sensitive metadata. Store the actual images in controlled private storage.

## Final selection

Target 30–50 high-quality, varied images for the first Person LoRA run. Cull duplicates and images that fail to contribute useful identity information.
