# MetaHuman Animator Plugin Overview

## 1. What this plugin does
- Provides the official MetaHuman Animator toolchain for capturing, processing, and solving facial/body data into MetaHuman assets.
- Includes identity creation/editing, face contour tracking, fitting and animation solvers, capture ingest utilities, and Sequencer integration.
- Supplies extensive editor UI, pipelines, and batch processing utilities for MetaHuman footage and configuration.
- Category: MetaHuman; primarily editor tooling with runtime support for certain trackers/solvers.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Extensive editor tooling for MetaHuman capture/solving plus runtime trackers/solvers and Sequencer integration.

## 3. Key Modules
- **MetaHumanCore** (Runtime) / **MetaHumanCoreEditor** (Editor): Core data structures, shared utilities, and editor integration.
- **MetaHumanIdentity** (Runtime) / **MetaHumanIdentityEditor** (Editor): Identity asset, parts/poses, promoted frames, and the identity asset editor.
- **MetaHumanFaceContourTracker** (Runtime) / **MetaHumanFaceContourTrackerEditor** (Editor): Face contour tracking and editor helpers.
- **MetaHumanFaceAnimationSolver** (Runtime) / **MetaHumanFaceAnimationSolverEditor** (Editor): Solves animation from tracked data to MetaHuman rigs.
- **MetaHumanFaceFittingSolver** (Runtime) / **MetaHumanFaceFittingSolverEditor** (Editor): Fitting pipelines for aligning facial geometry.
- **MetaHumanCaptureSource**, **MetaHumanCaptureDataEditor**, **MetaHumanFootageIngest**, **MetaHumanDepthGenerator**, **MetaHumanCaptureUtils**, **MetaHumanCaptureProtocolStack** (Editor): Capture ingestion, depth generation, and capture protocol utilities.
- **MetaHumanPerformance** / **MetaHumanSequencer** (Editor PostEngineInit): Performance review/Sequencer integration for captured MetaHuman data.
- **MetaHumanPipeline**, **MetaHumanToolkit**, **MetaHumanSpeech2Face**, **MetaHumanBatchProcessor**, **MetaHumanConfig**/**MetaHumanConfigEditor**, **MetaHumanPlatform**, **MetaHumanControlsConversionTest**, **MetaHumanImageViewerEditor**, **MeshTrackerInterface**: Supporting pipeline, config, conversion tests, and viewer modules.

## 4. Important Types & APIs
### Identity creation and editing
- `UMetaHumanIdentity`, `UMetaHumanIdentityPart` (+ `UMetaHumanIdentityFace/Body/Hands/Outfit/Prop`), `UMetaHumanIdentityPose`, `UMetaHumanIdentityPromotedFrame`: Define the identity asset, its poses, and promoted frames used for solving.
- `UMetaHumanIdentityViewportSettings`, `FMetaHumanIdentityStateValidator`: Viewport/render settings and asset validation.
- `FMetaHumanIdentityAssetEditorToolkit`, `SMetaHumanIdentityPartsEditor`, `SMetaHumanIdentityPromotedFramesEditor`: Asset editor UI to add parts/poses, capture frames, and drive contour solving.

### Tracking and solving
- `UMetaHumanFaceContourTracker`: Performs contour tracking on footage/promoted frames.
- `UMetaHumanFaceAnimationSolver` and `UMetaHumanFaceFittingSolver`: Solve animation/fitting from tracked contours to MetaHuman rigs.
- `UMetaHumanConfig`: Runtime configuration asset consumed by trackers/solvers; `UMetaHumanConfigEditor` provides editing UI.

### Capture and pipeline utilities
- Capture modules supply ingest and processing (`FMetaHumanFootageIngest`, `UMetaHumanDepthGenerator`, `MetaHumanCaptureProtocolStack` utilities).
- `MetaHumanPerformance`/`MetaHumanSequencer` integrate solved data with Sequencer for review; `MetaHumanSpeech2Face` handles speech-driven alignment.
- `MetaHumanBatchProcessor` automates pipeline tasks across multiple shots/frames.

## 5. Typical usage patterns
- Enable the plugin (MetaHuman category). Create a MetaHuman Identity asset and open it in the MetaHuman Identity editor.
- Import footage, promote frames, and run contour tracking; adjust head alignment and camera calibration within the editor widgets.
- Run fitting/animation solvers to produce MetaHuman-ready animation; review in Sequencer via the MetaHuman Performance/Sequencer modules.
- Use MetaHuman Toolkit/Batch Processor to automate capture-to-solve pipelines; tune `UMetaHumanConfig` for solver settings.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; the plugin is marked as the official MetaHuman Animator toolkit shipped with UE 5.7.
