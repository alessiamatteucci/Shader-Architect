---
name: shader-architect
description: Design, analyze, create and refine native Figma shaders from visual references or art direction. Use for procedural fills, material effects, controllable textures and shader corrections through Figma MCP, or for a technical shader brief when execution is unavailable.
---

# Shader Architect

Translate visual intent into controllable native Figma shaders. Respond in the user's language (Italian or English); write implementation briefs and code identifiers in English. Separate artistic intent, technical hypotheses and observed results.

## Choose the mode

Treat `/CREATE`, `/REFINE`, `/ANALYZE` as instructions in the conversation, not registered application commands. Infer the mode when the user speaks naturally.

- **/CREATE**: design and implement a new shader. Read [creation workflow](references/workflows.md#create). When a user asks for a prompt only, deliver the brief without executing it.
- **/REFINE**: make the requested change to an existing shader while preserving other successful properties. Read [refinement workflow](references/workflows.md#refine).
- **/ANALYZE**: examine a supplied image, description or source without changing Figma. Read [analysis workflow](references/workflows.md#analyze). An analysis request alone does not authorize creation.

For direct execution, read [Figma adapter](references/figma-mcp-workflow.md), discover the available official Figma MCP tools, and load the installed `figma-shaders` skill and its authoring reference before writing. Use their current contracts, not remembered API shapes. This skill provides creative decisions; the official skill provides the execution contract.

If execution or its required documentation is unavailable, produce a technical brief using [prompt template](references/prompt-template.md), state the missing dependency, and clearly label the result **brief only — not created in Figma**. Do not silently switch to a web app or Figma Make.

## Shared creative method

1. Extract the desired result, composition, palette, material, alpha behavior, motion, editable controls, target dimensions and hard constraints. Ask only for information that materially blocks a correct choice; otherwise state reasonable assumptions and proceed.
2. Inspect supplied references. Preserve specified silhouette, proportions, palette and composition. Distinguish directly visible properties from inferred techniques. A still image cannot establish animation or the original algorithm.
3. Choose `fill` for generated pixels or `effect` for transformation of an input raster. A fill cannot refract arbitrary content behind it. An effect's input does not automatically include all background layers.
4. Write a compact implementation brief and parameter table. Select only techniques that serve the result. Continue into implementation when creation is requested; the brief is not a mandatory approval checkpoint.
5. Validate both technical and visual results with [quality checks](references/quality-and-debugging.md). If no rendered preview is available, explicitly leave visual verification pending.

## Read only what is needed

- Coordinates, masks, procedural composition, loops: [fundamentals and patterns](references/fundamentals-and-patterns.md).
- Glass, chrome, liquid, holography and transparency: [materials and optics](references/materials-and-optics.md).
- Controls, range design and predictable changes: [parameter design](references/parameter-design.md).
- Runtime, metadata and source contracts: [Figma adapter](references/figma-mcp-workflow.md), then current official documentation.
- Example briefs: [iridescent glass](examples/iridescent-glass.md), [liquid chrome](examples/liquid-chrome.md), [holographic material](examples/holographic-material.md), [organic distortion](examples/organic-distortion.md), [animated noise](examples/animated-noise.md).

The examples are design recipes, not rendered references or prevalidated shaders. Do not adopt their palette or composition unless the user's brief calls for them.

## Delivery

For execution, report name, kind, exact returned ID, version if provided, useful controls, verification status and the official try-in-Figma link. Do not claim a shader is applied to a document or publicly published without evidence. For analysis, return observations, plausible techniques, limitations and a suggested next brief. For refinement, explain the targeted change and which properties were preserved.
