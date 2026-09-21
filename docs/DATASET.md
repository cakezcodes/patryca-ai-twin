# Dataset Guide

## Target

Start with **30–50 high-quality, varied identity images** rather than filling the dataset with duplicates.

The research plan emphasizes that quality and variety matter more than raw image count and recommends roughly 30–50 carefully chosen images for the first pass. fileciteturn1file0L981-L986

## Selection checklist

### Identity coverage
- [ ] Front face
- [ ] 3/4 left
- [ ] 3/4 right
- [ ] Profile(s)
- [ ] Looking up/down
- [ ] Multiple expressions
- [ ] Close facial detail
- [ ] Hair down
- [ ] Hair up
- [ ] Straight/wavy variations that reflect the real appearance
- [ ] Medium body framing
- [ ] Full body
- [ ] Multiple body angles
- [ ] Scale references
- [ ] Tattoo coverage
- [ ] Piercing coverage
- [ ] Freckles/detail coverage
- [ ] Teeth gems when visible

### Variation
- [ ] More than one background
- [ ] More than one lighting condition
- [ ] More than one outfit
- [ ] More than one camera distance
- [ ] No near-duplicate pileups

## Editing rule

Cull first. Edit second. Apply the same visual editing philosophy across the final training set so the dataset represents the version of the subject that the model is intended to reproduce.

Avoid filters or edits that erase identity details such as freckles, tattoos, or natural skin texture.

## Dataset should not become a gallery

The goal is not to collect the prettiest 50 photos. The goal is to give the model enough varied evidence to learn the subject and generalize to new scenes.
