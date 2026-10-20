# Figma execution adapter

Contract snapshot checked 20 October 2026 against the installed official Figma shader skill, its `references/authoring.md`, and exposed official MCP tool schemas. Re-read the live skill for execution: a snapshot is not a permanent API guarantee.

## Resolve dependencies

Prefer official Figma MCP. Discover `whoami`, `create_shader`, `get_shader`, `update_shader`, `list_shaders` as needed. Load the installed `figma-shaders` skill before create/update. If absent, use the provider's skill reader for `skill://figma/figma-shaders/SKILL.md` and `skill://figma/figma-shaders/references/authoring.md`. Do not hardcode a user's home folder or plugin version.

If canvas scripting is needed, load `figma-use` and the applicable official skills first. Library shader creation does not require building an unrelated canvas or UI.

## New shader

1. Resolve the owning plan from a supplied valid plan key or `whoami`. Follow the current tool's choice requirement; the checked schema requires asking which plan to use if more than one is available. Never fabricate a plan key.
2. Call `create_shader` once with name, description, `kind` and `planKey`. Save the returned ID immediately.
3. Call `get_shader` and read every returned source URI. Use `includeSource: true` only when resource reading is unavailable. If source is truncated, obtain the complete source before editing.
4. Read current authoring instructions, prepare the complete `main.ts`, then call `update_shader` with the same ID and kind, files and a specific commit message. Set animation/mouse metadata to match source usage.
5. Treat a non-error update response as build success. Record version if present; its omission alone is not failure. On compiler error, make a targeted fix and retry once. If that fails, report the exact error. On ambiguous transport failure, read the resource state before retrying; do not blindly create another shader.

For updates, resolve the ID using `list_shaders` if necessary, fetch current source, then follow steps 4–5. Only `main.ts` can be replaced in the checked schema; metadata-only edits may use an empty files array. Account-library deployment is not proof of public marketplace publication.

## Runtime invariants from the checked authoring contract

- TypeScript orchestrates WebGPU; WGSL contains GPU programs. GLSL examples require adaptation, not direct pasting.
- Only import `defineProperties` from `figma:shaders`. Keep its call at module scope; runtime variables/constants belong inside setup/render or `frame.state`, not top-level declarations.
- Use the scaffold's module contract, with default function, `setup(device, frame)` and `render(device, frame)`.
- Allocate format-independent resources in setup; cache pipelines by `frame.output.format` in render. Do not hardcode the output format.
- Bindings, uniform layout and writes must agree; uniform buffer sizes are multiples of 16 bytes. Writeable buffers require COPY_DST.
- Effects guard null input, sample it intentionally and use premultiplied alpha. Opacity scales full RGBA. Fills never bind input and use straight alpha; opacity scales alpha only.
- Start every complete WGSL module with `diagnostic(off,derivative_uniformity);`; use `vs_main` and `fs_main` entrypoints. Follow the official derivative and control-flow rules even with the diagnostic disabled.
- Use mutable `var` where needed; avoid GLSL builtins, multi-component swizzle assignment and invalid array syntax.
- Time is milliseconds: convert `Number(frame.time) * 0.001` for seconds. Reading time/frame requires `metadata.isAnimated: true`; reading mouse requires `metadata.usesMouse: true`. Set false when removing the last use.
- Runtime has no DOM, fetch, timers or browser globals. Do not assume external textures or host resources.
- If animation or mouse capability is rejected, stop that path; offer a static alternative with controls, optionally keyframed in Motion if supported. Do not bypass the gate or silently claim equivalent behavior.

## Try link

Use the exact returned ID and choose `gen_effect` for effect or `gen_fill` for fill:

`https://www.figma.com/file/new?try-tool-resource-content-id=ID&try-tool-resource-type=TYPE&type=design&mode=design`

Replace ID and TYPE before delivery. Follow the official skill's existing-file follow-up; use an actual provided file URL, never invent one. A try link makes the shader available to try; it does not prove that a specific layer was updated.
