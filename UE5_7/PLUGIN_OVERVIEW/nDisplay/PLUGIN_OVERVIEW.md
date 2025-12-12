# nDisplay Plugin Overview

## 1. What this plugin does

- Provides synchronized clustered rendering across multiple machines for large displays, domes, caves, and LED volumes.
- Manages projection policies, warp/blend, chroma/light card compositing, and viewport orchestration for ICVFX setups.
- Supplies media synchronization, remote control interception, and replication hooks for multi-node rendering.
- Ships with editor tooling (Configurator, Operator, Light Card Editor, Stage Monitoring) to author and control nDisplay stages.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor configurator/operator tools plus runtime clustered rendering, media sync, and ICVFX pipelines.

## 3. Key Modules

- **DisplayCluster** (Runtime) – Core cluster runtime (root actor, configuration loading, network sync, viewport/frame orchestration).
- **DisplayClusterProjection**, **DisplayClusterWarp**, **DisplayClusterShaders**, **DisplayClusterScenePreview** (Runtime) – Projection policies, warp/blend, and preview rendering.
- **DisplayClusterConfiguration** (Runtime) – Configuration asset types, versioning, and serialization helpers.
- **DisplayClusterMedia**, **DisplayClusterMediaEditor**, **DisplayClusterRemoteControlInterceptor**, **DisplayClusterReplication** (Runtime/Editor) – Media sync, remote control interception, replication hooks.
- **DisplayClusterOperator**, **DisplayClusterConfigurator**, **DisplayClusterEditor**, **DisplayClusterDetails**, **DisplayClusterColorGrading**, **DisplayClusterLightCardEditor**, **DisplayClusterLightCardEditorShaders**, **DisplayClusterStageMonitoring** (Editor) – Authoring UIs, details customizations, light card workflow, monitoring tools.
- **DisplayClusterFillDerivedDataCache** (Editor) – Precomputes derived data for nDisplay assets.
- **DisplayClusterMoviePipeline**, **DisplayClusterMoviePipelineEditor** (UncookedOnly/Editor) – Movie Render Queue integration.
- **DisplayClusterMultiUser** (UncookedOnly) – Multi-user collaboration support for cluster assets.
- **SharedMemoryMedia**, **SharedMemoryMediaEditor** (Runtime/Editor) – Shared-memory-based media IO helpers.
- **DisplayClusterTests** (UncookedOnly) – Test coverage for cluster code paths.

## 4. Important Types & APIs

### `ADisplayClusterRootActor`

- Central actor representing a cluster stage: owns viewports, camera components, configuration data, and sync components (`UDisplayClusterSyncTickComponent`).
- Holds `UDisplayClusterConfigurationData` describing node/view/projection layout and applies property overrides.

### `UDisplayClusterCameraComponent` / `UDisplayClusterICVFXCameraComponent`

- Camera components used for per-viewport rendering and ICVFX frustum control; support inner/outer frustums and nDisplay-specific projection tuning.

### `UDisplayClusterConfigurationData` & related structs (`DisplayClusterConfigurationTypes*`)

- Blueprintable configuration containers defining cluster nodes, viewports, projection policies, OCIO, media sync, and post-processing rules.

### `IDisplayCluster*` Interfaces (projection, warp, shaders, viewport, post process)

- Extensibility points for custom projection/warp/presentation policies; used by runtime modules and editor builders.

### `FDisplayClusterViewportManager`

- Runtime manager for creating/configuring viewports, applying post-processing/ICVFX settings, and coordinating render frame submission.

### Light card and stage helpers

- Types such as `ADisplayClusterLightCardActor`, `UDisplayClusterStageGeometryComponent`, and light-card editor interfaces power LED stage card workflows.

## 5. Typical usage patterns

- Author an nDisplay configuration asset in DisplayClusterConfigurator, then spawn an `nDisplay Root Actor` in the level bound to that asset.
- Configure projection/warp policies per viewport, OCIO/postprocess settings, and ICVFX camera frustums; preview via Scene Preview and Stage Monitoring.
- Use DisplayClusterOperator for runtime control (node status, color grading) and DisplayClusterLightCardEditor for card placement on LED volumes.
- Integrate media sync through DisplayClusterMedia outputs/inputs and SharedMemoryMedia when sharing frames with other processes.
- For rendering pipelines, enable the Movie Pipeline modules to drive cluster renders via Movie Render Queue.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific flags were found in the module descriptors or headers; the overview reflects the current 5.7 source layout.
