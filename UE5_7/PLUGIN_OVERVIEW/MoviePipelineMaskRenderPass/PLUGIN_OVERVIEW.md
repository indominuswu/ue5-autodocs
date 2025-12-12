# Movie Render Queue Additional Render Passes Plugin Overview

## 1. What this plugin does
- Adds extra render passes for Movie Render Queue, including Object ID/Cryptomatte-style output and panoramic stitching.
- Extends Movie Render Pipeline with blueprint-exposed image pass types.
- Provides Movie Graph nodes for configuring object ID output in graph-driven renders.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Movie Render Queue users add the Object ID and Panoramic passes (and Movie Graph node) directly when configuring jobs, making this an editor-facing rendering feature.

## 3. Key Modules
- **MoviePipelineMaskRenderPass** (UncookedOnly)
  - Role: Implements additional render passes and graph nodes for editor-side rendering workflows.
  - Notable types: `UMoviePipelineObjectIdRenderPass`, `UMoviePipelinePanoramicPass`, `UMovieGraphObjectIdNode`.

## 4. Important Types & APIs

### `UMoviePipelineObjectIdRenderPass`
- Role: Generates Object ID mattes (limited Cryptomatte-style) for Movie Render Queue shots.
- Key properties: `IdType` (object ID mode), `bIncludeTranslucentObjects`.
- Key functions: overrides render pass setup/teardown, view render target creation, and telemetry to integrate the pass.

### `UMoviePipelinePanoramicPass`
- Role: Produces stitched panoramic/equirectangular renders (supports stereo panes) from tiled views.
- Key properties: `NumHorizontalSteps`, `NumVerticalSteps` controlling pane tiling.
- Key functions: overrides render pass setup, view state handling, surface queue creation, and pass output ordering.

### `UMovieGraphObjectIdNode`
- Role: Movie Graph node that exposes Object ID pass configuration when using graph-based render setups.

## 5. Typical usage patterns
- Enable the plugin, open Movie Render Queue, and add “Object Ids (Limited)” or “Panoramic Rendering” passes to a render config.
- For Movie Graph workflows, insert `MovieGraphObjectIdNode` to emit Object ID outputs.
- Configure object ID settings (ID type, inclusion of translucency) or panoramic tiling counts per job.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

