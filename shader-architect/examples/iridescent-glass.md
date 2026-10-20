# Iridescent glass

Design recipe, not a compiled or visually verified shader.

## Create brief

```text
/CREATE
Kind: effect
Create sparse organic glass droplets that distort the supplied input raster. Keep the input recognizable; use delicate pink/cyan spectral highlights confined mainly to curved edges. Preserve transparent areas outside the droplets.
Controls: Size, spacing, deterministic seed, distortion in pixels, tint, highlight width, iridescence strength.
```

## Compatibility and quality

Do not claim the effect can see unrelated background layers. Check the actual input raster first.

## Targeted refinement

```text
/REFINE [actual shader ID]
Reduce iridescence by half without changing geometry, seed, alpha, distortion or animation.
```
