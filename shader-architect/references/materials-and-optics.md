# Materials and optics

## Glass and translucent liquid

First distinguish transparent outside the shapes, translucent inside them, and distorted content seen through them. These are separate requirements. Lower opacity alone is not refraction.

For visible background distortion, use an effect sampling the actual input raster. Verify that the desired content is present in that raster. A procedural fill can depict stylized glass using contour, highlight and color cues, but cannot sample arbitrary underlying layers.

Use a shape field to estimate surface direction and concentrate reflection near grazing angles. Fresnel-like weighting can use `F0 + (1-F0)*(1-cosTheta)^5`; in a 2D approximation the normal/view estimate is artistic, not evidence of physical simulation. Derive distortion from coherent gradients and bound displacement. Separate tint, distortion, highlight width, iridescence and alpha controls.

For “too plastic,” inspect broad diffuse-looking color, uniform opacity and disconnected highlights before changing all controls. For “opaque glass,” inspect alpha convention and input visibility first. Realistic transmission also depends on the background and compositing context.

## Chrome and metal

Readability comes from coherent reflected light/dark structures following the surface. Use an explicit procedural environment approximation when no environment texture exists. Roughness should broaden and soften reflections rather than merely lower opacity. Keep opacity near solid unless transparency was requested. Describe this as stylized/procedural reflection unless a physical rendering model is actually implemented.

## Iridescence and holography

Tie hue variation to curvature, viewing proxy or a designed spatial phase. Localize spectral color to relevant contours/highlights to avoid a uniform rainbow wash. Keep iridescence strength independent of transparency and geometry. A sinusoidal palette is an artistic approximation, not a thin-film interference simulation.

Distinguish holographic foil, pearlescent material and RGB channel separation: they have different appearance and controls. Chromatic dispersion changes sampling offsets by channel; it can damage text readability and alpha edges if exaggerated.

## Fluid appearance

Low-frequency smooth deformation, coherent highlights and continuous motion can suggest liquid. Noise-driven motion is not a fluid simulation. Preserve volume cues by controlling how silhouette and highlight fields move together.
