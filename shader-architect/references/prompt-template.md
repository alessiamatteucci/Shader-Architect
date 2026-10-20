# Technical brief template

Use English for the implementation brief, with a short explanation in the user's language. Remove irrelevant sections.

```text
NAME:
MODE: CREATE / REFINE / ANALYZE
TARGET: Native Figma shader
KIND: fill / effect, with input-raster rationale
VISUAL RESULT: Composition, silhouette, palette and material cues.
REFERENCE CONSTRAINTS: Visible properties to preserve; inferred techniques separately.
CONSTRUCTION: Coordinates, shapes, masks and the simplest suitable procedural method.
OPTICS AND ALPHA: Input content, distortion, highlights, straight/premultiplied contract.
CONTROLS: Key, type, range, step, default, unit, behavior and independence.
MOTION: Static or time-based, speed, amplitude, continuity and loop requirement.
RUNTIME: Current official Figma contract, resource/binding plan and metadata flags.
ACCEPTANCE: Observable result, control extremes, alpha edges and target aspect ratios.
PRESERVE (REFINE): Existing properties that must not change.
LIMITATIONS: Approximation, missing inputs or unverified capability.
```

For prompt-only delivery, say explicitly that this is a specification for an agent with the Figma shader workflow, not executable WGSL or a guarantee that an arbitrary text field can generate it.
