# Verification and refinement

Keep three statuses separate: source/build validation, rendered appearance, and user acceptance. A successful update proves only the build/deployment result reported by the tool.

## Review a real preview when available

- Compare composition, silhouette, palette and material against the supplied reference.
- Check alpha over light, dark and detailed content where relevant. Watch for black fringes, unintended full-frame opacity and double premultiplication.
- Inspect min/default/max of key controls; check their intended independence.
- Compare the target aspect ratio and another meaningful size for stretched circles, noise scale and clipping.
- For animation, inspect more than one time and any requested loop seam. A still screenshot cannot validate motion.
- Report performance measurements only when measured. If unavailable, report qualitative cost risks without inventing FPS.

If preview access is missing, deliver the build and try link with “visual verification pending” and ask for a screenshot or inspection result when refinement depends on it. Do not substitute a generated illustration for the actual shader render.

## Diagnose selectively

| Symptom | Inspect first | Targeted correction |
| --- | --- | --- |
| Glass looks opaque | Input availability, alpha, tint | Fix compositing before adding highlights |
| Rainbow overwhelms form | Spectral mask and saturation | Localize and reduce iridescence |
| Black edge halos | Premultiplication and sampling bounds | Apply the kind-specific alpha contract |
| Shape changes with speed | Seed/time coupling | Separate spatial randomness from phase |
| Banding or shimmer | Precision, frequency, edge filtering | Reduce high-frequency detail or filter masks |
| Slow rendering | Sample count, loops, allocations | Reduce redundant work; cache stable resources |
| Blank output | Compiler, bindings, target format, input guard | Fix the evidenced failure before redesign |

Preserve the previous version/source before edits. Respect the official one-correction retry limit for build failures and terminal animation/mouse capability gates. If an update response is ambiguous, inspect state before repeating the mutation.
