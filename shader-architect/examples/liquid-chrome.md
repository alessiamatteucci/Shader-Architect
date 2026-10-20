# Liquid chrome

Design recipe, not a compiled or visually verified shader.

## Create brief

```text
/CREATE
Kind: fill
Create a coherent liquid-metal surface with broad dark and bright reflection bands following smooth organic curvature. Use a procedural environment approximation and a solid surface.
Controls: Shape scale, deformation amount, roughness proxy, reflection contrast, tint, seed, optional speed.
```

## Compatibility and quality

Do not call noise deformation a fluid simulation or a procedural environment a real scene reflection.

## Targeted refinement

```text
/REFINE [actual shader ID]
Broaden highlights without changing silhouette, palette, seed or motion speed.
```
