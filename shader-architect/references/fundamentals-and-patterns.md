# Procedural construction

## Coordinates and scale

Define whether controls use local pixels, normalized UV or percent. Correct aspect ratio for circles and isotropic noise; otherwise changing layer width stretches geometry. Separate UV used for raster sampling from centered coordinates used for shape generation. Preserve visual scale deliberately when resizing.

## Choose the simplest useful building blocks

| Visible goal | Candidate | Main control | Failure to check |
| --- | --- | --- | --- |
| Soft blobs | SDF circles/ellipses plus smooth union | Radius, spacing, blend width | Blobs merge and erase negative space |
| Cellular pattern | Voronoi distances | Cell scale, jitter, seed | Repeated grid and unstable cell edges |
| Organic texture | A few bounded noise octaves | Scale, detail, contrast | Fine noise dominates the material |
| Flowing deformation | Low-frequency domain warp | Amount, warp scale | Folding, excessive distortion |
| Ribs or bands | Periodic field plus smooth mask | Spacing, orientation, width | Aliasing at small sizes |
| Grain | Seeded high-frequency variation | Amount, grain scale | Flicker or dirty alpha edges |

A pseudo-random seed should change arrangement reproducibly; do not tie it to time unless flicker is intended. More octaves are not automatically better. Bound loop counts and test the actual target resolution before claiming performance.

## Masks and edges

Use a signed-distance or smooth scalar field to separate geometry from shading. Use a small, ordered smooth transition near the boundary; derivative-based antialiasing where the runtime permits. Do not use blurred geometry as a substitute for all antialiasing. Check small and large shapes for bright fringes and alpha halos.

## Animation

Use absolute time for stable playback. To guarantee a loop of duration T, drive all animated components through periodic phase 2πt/T or a suitable periodic noise domain. Translating arbitrary noise linearly does not guarantee a seamless loop. Test both image and velocity around the seam when smooth motion matters.

At speed zero, preserve a useful static appearance. Keep shape seed independent of animation speed so speed edits do not randomize the composition. Avoid accumulated frame steps where skipped rendering would change the result.
