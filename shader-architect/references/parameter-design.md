# Parameter design

For each control specify: label, stable key, supported type, range, step, default, unit, visible behavior at the extremes, dependencies and properties it must not change. Start with a compact useful set; add controls when they express a distinct user decision.

Separate geometry (size/count/seed), material (tint/roughness/distortion), optics (highlight/iridescence), composition and motion. Avoid making “Intensity” change every category at once. Keep seed deterministic, and preserve existing keys and defaults during a targeted refinement.

## Mapping into the checked Figma contract

Use native `number`, `boolean`, `color` and supported geometric/gradient controls. Integer and seed concepts may be bounded stepped numbers; do not invent `integer` or `seed` schema types. Select controls use numeric values, not string selects. Colors use channels 0–1. Read current authoring docs for exact nested shapes.

Positions in percent become UV by dividing by 100. Pixel units stay absolute. Percent radius for a point-radius control is relative to the smaller layer dimension in the checked contract.

## Example design table (not API JSON)

| Key | Control | Range/default | Intended independence |
| --- | --- | --- | --- |
| size | number, percent | 5–40, 16 | No change to hue or speed |
| seed | stepped number | 0–9999, 17 | Changes arrangement, not palette |
| iridescence | number | 0–1, 0.15 | No change to alpha or silhouette |
| distortion | number, pixels | 0–24, 6 | No seed randomization |
| speed | number, cycles/second | 0–0.5, 0.06 | Zero freezes a useful frame |

These ranges are starting points for an example, not universal limits. Use perceptual remapping where necessary and explain non-linear behavior. Check min/default/max and important pairs, especially density × size or distortion × curvature. Bound denominators and avoid singularities at zero.
