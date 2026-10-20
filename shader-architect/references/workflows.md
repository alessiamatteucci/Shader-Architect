# Mode workflows

## CREATE

1. Convert the brief into observable acceptance criteria: e.g. broad highlights, sparse organic shapes, transparent outside the shapes, no rainbow across the whole surface.
2. If an image is supplied, inspect it before choosing techniques. If the image is unavailable, request it or proceed explicitly from text only.
3. Choose fill/effect based on input requirements. Decide whether a single shader can deliver the composition or whether additional layers are needed.
4. Read relevant material/pattern guidance. Propose a small useful control set, units, bounded ranges and defaults. Identify exact versus approximate behavior.
5. Follow the Figma adapter through the completed source update. Do not stop at the scaffold.
6. Review a real rendered result when available. Test meaningful control extremes and target aspect ratios. Correct actual failures within the execution retry limits.
7. Deliver the shader identity and link, with separate build and visual status.

## REFINE

1. Resolve an exact shader ID. If only a name is known, list shaders and resolve ambiguity before updating. A screenshot alone is not an editable shader identity.
2. Fetch current metadata and every source file. Keep the prior source and returned version available for comparison/recovery. Do not use an older conversation fragment as the latest source.
3. Describe the intended delta and preserved properties. Example: reduce iridescence while keeping geometry, alpha, seed, speed and control names.
4. Distinguish evidence from likely cause. Inspect the source or compare a preview before asserting a diagnosis.
5. Change the smallest relevant part and send the full replacement `main.ts`. Preserve kind and controls unless the user asked otherwise. If the goal requires another kind, explain the need for a separate shader rather than updating with a mismatched kind.
6. Compare before/after with the same seed, layer dimensions, parameter values and time. Check the requested improvement and preserved invariants.
7. Report what changed and remaining limits. If a build fails twice, retain the error and proposed correction rather than creating duplicate resources.

## ANALYZE

Produce a compact table: visible feature / evidence / possible technique / confidence or limitation. Cover only relevant geometry, optical behavior, palette, lighting, alpha, texture and composition. Describe motion only when footage or an explicit motion brief supplies evidence.

Separate three levels:
- **Observed**: a narrow bright contour, distorted lettering, nonuniform cell sizes.
- **Inferred**: Fresnel-like weighting, UV displacement, seeded Voronoi.
- **Unproven**: real 3D geometry, physical IOR, actual thin-film simulation, exact noise algorithm.

Conclude with fill/effect choice, controllable parameters and an English implementation brief if useful. Do not mutate account resources in this mode without an additional request to create or refine.
