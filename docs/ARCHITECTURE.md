# Architecture

## Identity layer

The Person LoRA is the identity layer. It is responsible for stable visual traits that should follow the subject across scenes:

- Facial structure
- Eye color
- Hair color/style identity
- Freckles
- Tattoos
- Piercings
- Teeth gems
- Body proportions
- Other distinctive physical marks

The research plan explicitly recommends centralizing stable identity features in one Person LoRA instead of splitting personal features across multiple overlapping LoRAs. fileciteturn1file0L663-L675

## Reference layer

Reference conditioning is for visual information that changes by scene or needs a direct visual example:

- Specific lingerie/clothing
- Jewelry
- Room/environment
- Props
- Other transient visual concepts

## Generation layer

ComfyUI combines the identity layer, reference layer, prompt, sampling, and final correction/upscaling into the generation workflow.

## Design principle

**Learn identity once. Reference changing things when needed.**

This keeps the system easier to maintain and reduces the identity conflicts associated with stacking many specialized personal LoRAs.
