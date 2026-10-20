# Organic distortion

Design recipe, not a compiled or visually verified shader.

## Create brief

```text
/CREATE
Kind: effect
Distort the supplied raster using a smooth low-frequency vector field. Keep central content recognizable and bound the displacement. Preserve input alpha.
Controls: Distortion pixels, field scale, seed, center, falloff, optional speed.
```

## Compatibility and quality

Inspect readability and clamp sampling bounds unless transparent out-of-bounds behavior is intended.

## Targeted refinement

```text
/REFINE [actual shader ID]
Reduce displacement around the center without changing the outer flow or seed.
```
