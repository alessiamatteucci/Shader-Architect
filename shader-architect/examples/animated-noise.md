# Animated noise

Design recipe, not a compiled or visually verified shader.

## Create brief

```text
/CREATE
Kind: fill
Create a soft two-color organic noise field with slow continuous motion and a useful static state. If a seamless loop is requested, use a periodic time domain throughout.
Controls: Two colors, scale, contrast, warp amount, speed, seed; loop duration only if implemented.
```

## Compatibility and quality

Animation requires the verified capability and isAnimated metadata. Linear noise translation alone does not guarantee a loop.

## Targeted refinement

```text
/REFINE [actual shader ID]
Slow the motion without changing spatial scale, seed, contrast or palette.
```
