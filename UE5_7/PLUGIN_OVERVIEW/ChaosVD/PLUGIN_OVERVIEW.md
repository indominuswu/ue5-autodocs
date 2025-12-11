# Chaos Visual Debugger Plugin Overview

## 1. What this plugin does

- Enables visual debugging of Chaos physics simulations with capture, playback, and rich visualization of solver data.
- Provides editor/program tooling for exploring particle, constraint, collision, and scene query data.
- Includes Blueprint-accessible extensions and built-in visualization settings for multiple Chaos data types.

## 2. Key Modules

- **ChaosVD** (EditorAndProgram)  
  - Role: Core visual debugger runtime/editor tooling, UI, and data capture/playback pipeline.
  - Notable types: `UChaosVDCoreSettings`, `UChaosVDGeneralSettings`, `UChaosVDExtensionsManager`, `UChaosVDTraceManager`, multiple visualization settings classes.
- **ChaosVDBlueprint** (RuntimeAndProgram)  
  - Role: Blueprint-facing hooks and helpers for Chaos Visual Debugger integration.
- **ChaosVDBuiltInExtensions** (EditorAndProgram)  
  - Role: Built-in extensions and component visualizers for common Chaos data sets.

## 3. Important Types & APIs

### Settings and managers
- `UChaosVDCoreSettings`, `UChaosVDGeneralSettings`, `UChaosVDMiscSettings`: configure capture/playback, storage, and visualization defaults.
- `UChaosVDExtensionsManager`: registers and manages debugger extensions.
- `UChaosVDTraceManager`: handles tracing/capture of Chaos data streams.

### Visualization components & data
- Data components: `UChaosVDParticleDataComponent`, `UChaosVDSolverDataComponent`, `UChaosVDSolverCollisionDataComponent`, `UChaosVDSolverJointConstraintDataComponent`, `UChaosVDSceneQueryDataComponent`, `UChaosVDSolverCharacterGroundConstraintDataComponent`, `UChaosVDGTAccelerationStructuresDataComponent`.
- Visualizers/settings: `UChaosVDCollisionVisualizationSettings`, `UChaosVDJointConstraintVisualizationSettings`, `UChaosVDParticleVisualizationSettings`, `UChaosVDAccelerationStructureVisualizationSettings`, `UChaosVDSceneQueryVisualizationSettings`, `UChaosVDGenericDebugDrawSettings`.
- Components/visualizers: `UChaosVDInstancedStaticMeshComponent`, `UChaosVDStaticMeshComponent`, `UChaosVDGenericDebugDrawDataComponent` (+ visualizers), `UChaosVDGeometryDataComponent`.

### Editor tools
- `UChaosVDEditorMode` and `UChaosVDEditorModeTools`: editor mode for inspecting captures.
- Customizations/factories: `FChaosVDGeometryComponentCustomization`, `FChaosVDCustomIconDataStorageFactory`, `FChaosVDParentDataStorageFactory`, `FChaosVDParticleEditorDataFactory`.

## 4. Typical usage patterns

- Enable Chaos Visual Debugger to capture Chaos simulation data during PIE or runtime, then open captures in the editor mode.
- Adjust visualization settings (collision, joint constraints, particles, acceleration structures) to inspect specific simulation aspects.
- Use the trace manager and extensions to record solver events; view data through provided component visualizers and instanced mesh representations.
- Leverage Blueprint hooks from `ChaosVDBlueprint` for integrating capture triggers or playback controls in tools.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
