# Color Correction Regions (CCR) Plugin Overview

## 1. What this plugin does
- Provides region/volume-based color correction that blends via post-process materials.
- Supports multiple shapes (sphere, box, cylinder, cone) with controllable priority, falloff, and color grading controls.
- Aggregates and ticks regions through an engine subsystem to keep assignments and stencil IDs in sync, including editor undo/redo.
- Integrates with nDisplay stage actors for virtual production workflows.

## 2. Key Modules
- **ColorCorrectRegions** (Runtime)  
  - Role: Implements the region actor, scene view extension, post-process material setup, and the world subsystem that tracks active regions.
- **ColorCorrectRegionsEditor** (Editor)  
  - Role: Details customizations, style assets, context menus, and color grading hierarchy integrations for editing CCR actors.

## 3. Important Types & APIs

### `AColorCorrectRegion`
- Role: Actor representing a bounded region that applies graded color correction via post-process. Supports sphere/box/cylinder/cone shapes and windowed CCR.
- Key properties: `Intensity`, `Inner`/`Outer`, `Falloff`, `Priority`, `Invert`, temperature controls, `ColorGradingSettings`, `PriorityBias`.
- Notes: Implements `IDisplayClusterStageActor` for stage-aware workflows; maintains mesh components for visualization.

### `UColorCorrectRegionsSubsystem`
- Role: `UTickableWorldSubsystem` that tracks CCR actors, handles actor add/remove/undo/redo events, assigns stencil IDs, and drives the CCR scene view extension each tick.
- Key functions: `OnActorSpawned`, `OnActorDeleted`, `AssignStencilIdsToPerActorCC`, `ClearStencilIdsToPerActorCC`, `CheckAssignedActorsValidity`.

### `FColorCorrectRegionsSceneViewExtension`
- Role: Scene view extension that injects CCR post-process passes for all active regions each frame.

### `FColorCorrectRegionsStencilManager`
- Role: Helper that allocates and validates stencil IDs used by CCR rendering.

## 4. Typical usage patterns
- Editor: Enable the plugin, place `Color Correct Region` actors in the level, choose a shape, and tune intensity/falloff/color grading. Editor customizations expose CCR parameters and color grading hierarchy entries.
- Runtime: Regions are auto-aggregated by `UColorCorrectRegionsSubsystem`; no manual registration needed. Stencil IDs are managed automatically unless overridden.
- Virtual production: Works with nDisplay stage actors; window CCR uses priority-by-distance for camera-facing correction.

## 5. Version-specific notes (UE 5.7)
- Some deprecated helpers reference earlier versions (e.g., deprecated stencil refresh functions), but no 5.7-specific behavior is called out in the sources. This overview reflects the current UE 5.7 code.
