# Performance Capture Core Plugin Overview

## 1. What this plugin does
- Supplies core actor components and utilities for performance capture workflows driven by Live Link.
- Provides retargeting helpers so captured animation can drive local skeletal meshes during recording/playback.
- Includes editor support for configuring capture actors and validating retargeting setups.

## 2. Key Modules
- **PerformanceCaptureCore** (Runtime)  
  - Runtime components and data structures for performance capture.  
  - Notable types: `UPerformerComponent`, `URetargetComponent`, `URetargetAnimInstance`, `FCapturePerformer`, `FCaptureCharacter`.
- **PerformanceCaptureCoreEditor** (Editor)  
  - Editor helpers/settings for the runtime components (details customizations and validation tools).

## 3. Important Types & APIs

### `UPerformerComponent`
- Role: Actor component that binds a Live Link subject (animation role) to a controlled skeletal mesh; can force other meshes on the owner to follow the driven mesh.
- Key properties/APIs: `SubjectName`, `ControlledSkeletalMesh`, `SetLiveLinkSubject`, `SetEvaluateLiveLinkData`, `GetEvaluateLiveLinkData`.

### `URetargetComponent`
- Role: Component that retargets animation from a source skeletal mesh (often Live Link driven) to target meshes, supporting face/body separation and pose offsets.
- Key properties: source/target mesh references, body/face pose search assets, pose offsets; runtime ticking to propagate transforms.

### `URetargetAnimInstance`
- Role: Anim instance used during capture to play retargeted animation on the target skeletal mesh; integrates with `URetargetComponent`.

### Data structs (`FCapturePerformer`, `FCaptureCharacter`)
- Role: Describe performer metadata and mapping between captured sources and target meshes during a capture session.

## 4. Typical usage patterns
- Enable the plugin (Animation category). Add `UPerformerComponent` to an actor, assign the Live Link subject and the skeletal mesh to drive.
- Add `URetargetComponent` to route the driven pose to other meshes (e.g., body vs face rigs); configure pose offsets and optional pose search assets for better matching.
- Use `URetargetAnimInstance` on the driven mesh to evaluate retargeted animation during recording or live preview.
- Editor module exposes details panels to configure performer/character mappings before a capture session.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
