# MetaHuman Core Tech Plugin Overview

## 1. What this plugin does
- Core technology stack shared by MetaHuman Creator and MetaHuman Animator, including capture data structures, pipelines, and image viewers.
- Supplies runtime libraries for platform/config data plus editor modules for viewing image data and pipeline integration.
- Forms a dependency for other MetaHuman plugins (Animator, Creator, SDK).

## 2. Editor/Runtime surfaces

- User-facing: No - Shared infrastructure/data types for other MetaHuman plugins; no standalone editor tools or gameplay APIs intended for direct user use.

## 3. Key Modules
- **MetaHumanCoreTechLib** (Editor)
  - Role: Editor-side library and integration glue for MetaHuman core tech; exposes shared headers and utilities.
- **MetaHumanCoreTech** (Runtime)
  - Role: Runtime data structures and utilities for MetaHuman processing (tracking data, frame data, transforms).
  - Notable types: `FAudioDrivenAnimationMood`, `FFrameAnimationData`, `FFrameTrackingContourData`, `FMetaHumanHeadTransform`, `FMetaHumanMeshData`, `FMetaHumanCommonDataUtils`.
- **MetaHumanImageViewer** (Runtime)
  - Role: Runtime image viewing utilities used by higher-level MetaHuman viewers.
- **MetaHumanCaptureData** (Runtime)
  - Role: Capture data containers used across MetaHuman pipelines.
- **MetaHumanPipelineCore** (Editor)
  - Role: Editor integration for pipeline utilities built on the core tech.
- **MetaHumanCoreTechLib** (Editor module listed in `.uplugin` as well): Provides the editor side for the runtime library.

## 4. Important Types & APIs
### Core data types
- `FFrameAnimationData`, `FFrameTrackingContourData`, `FFrameTrackingConfidenceData`: Structures describing frame-level tracking and animation data.
- `FMetaHumanHeadTransform`, `FMetaHumanMeshData`: Shared structs used when transferring solved data between modules.
- `FAudioDrivenAnimationMood`: Helper for audio-driven animation states.

### Utilities
- `MetaHumanCommonDataUtils` and `CoreUtils` provide helpers for converting GUI controls to raw controls, managing mesh data, and diagnostics (`FDepthMapDiagnosticsResult`).

## 5. Typical usage patterns
- Enable as a dependency of other MetaHuman plugins; it is not typically used directly by end users.
- Other MetaHuman modules consume the data structs and utilities during capture, solving, and asset generation.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; the plugin is disabled by default and serves as shared infrastructure.

