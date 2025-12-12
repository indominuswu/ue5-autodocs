# Procedural Content Generation Framework (PCG) Plugin Overview

## 1. What this plugin does

- Provides a graph-driven framework for procedurally populating worlds with content at edit time and/or runtime.
- Adds PCG components/volumes that execute PCG graphs to generate meshes, actors, and other data sources.
- Supplies editor tools for authoring PCG graphs, inspecting execution, and baking results.
- Includes optional compute features for GPU-assisted operations.

## 2. Editor/Runtime surfaces
- User-facing: Yes - PCG graph editor plus runtime components/volumes and Blueprint-accessible execution.

## 3. Key Modules

- **PCG** (Runtime)  
  - Role: Core PCG framework, data types, components, execution graph, and runtime scheduling.
- **PCGEditor** (Editor)  
  - Role: Graph editor UI, commands, editor settings, and level-to-asset conversion tools.
- **PCGCompute** (Runtime)  
  - Role: Compute-specific utilities (e.g., texture readback) for GPU-accelerated PCG tasks.

## 4. Important Types & APIs

- `UPCGComponent` (`PCGComponent.h`)  
  - Actor component that owns and runs a PCG graph, manages seed/state, and writes generated outputs.
- `UPCGGraph` / `UPCGNode` / `UPCGPin` (`PCGGraph.h`, `PCGNode.h`, `PCGPin.h`)  
  - Graph definition consisting of nodes and pins representing PCG operators and data flow.
- `UPCGSettings` / `UPCGSettingsWithDynamicInputs` (`PCGSettings.h`)  
  - Base settings for PCG nodes/operators; encapsulate parameters and dynamic input configuration.
- `UPCGData` and derivatives (`PCGData.h`, `PCGPoint.h`, `UPCGPointArray`)  
  - PCG data payload types passed between nodes (points, params, assets, etc.).
- `UPCGSubsystem` (`PCGSubsystem.h`)  
  - World subsystem coordinating execution, scheduling, and cache management across PCG components.
- `APCGWorldActor`, `APCGVolume` (`PCGWorldActor.h`, `PCGVolume.h`)  
  - Actor/volume wrappers that embed a PCG component for level placement and volume-bound generation.
- `FPCGGraphExecutionState`, `FPCGGraphExecutionInspection`  
  - Execution state/inspection helpers for debugging and visualization.
- `UPCGEditorSettings`, `FPCGEditorModule`  
  - Editor configuration for graph UI, commands, and asset conversion tools.

## 5. Typical usage patterns

- Enable the plugin and add a `PCGComponent` (or `PCGVolume`/`PCGWorldActor`) to a level actor; assign a PCG graph asset.
- Author PCG graphs in the PCG graph editor (nodes define sampling, filtering, spawning, etc.); adjust `UPCGSettings` per node.
- Run graphs in-editor for preview/baking or at runtime for dynamic generation; the subsystem schedules execution and manages generated components.
- Use editor inspection tools to visualize graph execution and data flow; convert level content to PCG assets via editor utilities.
- Optional compute features can be enabled for GPU-assisted tasks; `PCGCompute` supports texture readbacks and related operations.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current PCG implementation in the UE 5.7 source tree.
