# Movie Render Queue Plugin Overview

## 1. What this plugin does
- Provides the high-quality Movie Render Queue system for rendering sequences or automation jobs.
- Supplies runtime configs, executors, and output builders plus numerous render pass implementations.
- Adds editor UI/workflows for queue management, presets, and movie graph authoring.
- Includes MP4 encoding support and OpenEXR RTTI helpers for pipeline outputs.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Movie Render Queue/Graph editor UI plus runtime pipeline configs, executors, and Blueprint APIs.

## 3. Key Modules
- **MovieRenderPipelineCore** (Runtime)
  - Role: Core pipeline objects (jobs, queue, executors, configs, settings) and Movie Graph runtime types.
  - Notable types: `UMoviePipelineExecutorShot`, `UMoviePipelineExecutorJob`, `UMoviePipelineQueue`, `UMoviePipelinePrimaryConfig`, `UMoviePipelineShotConfig`, `UMoviePipelineBlueprintLibrary`, `UMoviePipelineQueueEngineSubsystem`, Movie Graph node/pin/config classes.
- **MovieRenderPipelineSettings** (Runtime)
  - Role: Project/editor render settings (burn-ins, console variables, widget rendering).
  - Notable types: `UMoviePipelineBurnInSetting`, `UMoviePipelineConsoleVariableSetting`, `UMoviePipelineWidgetRenderSetting`.
- **MovieRenderPipelineRenderPasses** (Runtime)
  - Role: Built-in render passes and outputs (deferred passes, EXR/image sequence, wave audio) plus Movie Graph render pass nodes.
  - Notable types: `UMoviePipelineDeferredPassBase`, `UMoviePipelineImageSequenceOutput`, `UMoviePipelineEXROutput`, MovieGraph deferred/panoramic/path tracer pass nodes.
- **MovieRenderPipelineEditor** (Editor)
  - Role: Editor UI for Movie Render Queue/Graph, asset definitions, preset editors, and Sequencer integration.
- **MovieRenderPipelineMP4Encoder** (Runtime)
  - Role: Command-line MP4 encoding and output utilities for rendered image sequences.
- **UEOpenExrRTTI** (Runtime)
  - Role: OpenEXR RTTI support used by pipeline EXR outputs.

## 4. Important Types & APIs

### `UMoviePipelineQueue` / `UMoviePipelineExecutorJob`
- Role: Define a queue of render jobs (sequences, maps) and per-job shot data (`UMoviePipelineExecutorShot`).
- Key functions: job/shot status reporting, shot override configs, blueprint exposure for automation.

### `UMoviePipelinePrimaryConfig` and `UMoviePipelineShotConfig`
- Role: Hierarchical configuration assets describing output formats, render passes, camera/AA/high-res settings.
- Key properties: output settings (`UMoviePipelineOutputSetting`), view family settings, AA/high-res settings, custom render passes.

### `UMoviePipelineExecutorBase` derivatives
- Role: Execute jobs either in-process or via external/pipeline-specific paths.
- Notable classes: `UMoviePipelineInProcessExecutor`, `UMoviePipelinePythonHostExecutor`, `UMoviePipelineLinearExecutor`; expose status/progress delegates for automation.

### `UMoviePipelineBlueprintLibrary`
- Role: Blueprint API for scheduling renders, manipulating queues, and querying pipeline status.

### Movie Graph types
- Role: Node-based authoring for pipeline configs.
- Notable types: `UMovieGraphConfig`, `UMovieGraphNode` (and many derived nodes for render passes, outputs, game overrides, metadata), `UMovieGraphProjectSettings`, `UMovieGraphRenderLayerSubsystem`.

### Output and render pass classes
- Role: Built-in render targets and outputs.
- Examples: `UMoviePipelineDeferredPassBase` (deferred renderer), `UMoviePipelineImagePassBase`, `UMoviePipelineEXROutput`, `UMoviePipelineImageSequenceOutput`, `UMoviePipelineWaveOutput`.

## 5. Typical usage patterns
- Enable the plugin and open Movie Render Queue to render Level Sequences or Movie Render Graph configs with high-quality settings.
- Create `MoviePipelinePrimaryConfig`/`ShotConfig` assets to define passes, outputs, AA/high-res tiling, burn-ins, and console variable overrides.
- Build queues via UI or Blueprint (`UMoviePipelineQueue` + `UMoviePipelineBlueprintLibrary`), then execute with in-process or Python-host executors for automation.
- Use Movie Graph authoring to set up node-based render pipelines and pass configurations, including layer/render pass selection and metadata nodes.
- MP4 encoding can be added via the MP4 encoder module when rendering image sequences that need packaged video output.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
