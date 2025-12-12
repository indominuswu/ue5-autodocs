# World Partition HLOD Utilities Plugin Overview

## 1. What this plugin does
- Provides editor utilities and builders for generating HLOD data in World Partition worlds.
- Adds HLOD builder implementations for mesh merging, simplification, instancing, approximation, and custom actors.
- Includes a modifier for HLOD mesh destruction behavior.
- Enabled by default and editor-only.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor HLOD builder/modifier utilities that teams select when generating World Partition HLOD data (merge/simplify/approximate/instancing/custom actor/destruction options).

## 3. Key Modules
- **WorldPartitionHLODUtilities** (Editor)
  - Role: Registers HLOD builders/modifiers and exposes utility helpers for World Partition HLOD workflows.
  - Notable types: `WorldPartitionHLODUtilitiesModule`, builders (`HLODBuilderMeshMerge`, `HLODBuilderMeshSimplify`, `HLODBuilderMeshApproximate`, `HLODBuilderInstancing`, `HLODBuilderCustomHLODActor`), modifier `HLODModifierMeshDestruction`.

## 4. Important Types & APIs
### `WorldPartitionHLODUtilities`
- Role: Utility functions for HLOD processing and registration in editor.

### `HLODBuilderMeshMerge`, `HLODBuilderMeshSimplify`, `HLODBuilderMeshApproximate`, `HLODBuilderInstancing`, `HLODBuilderCustomHLODActor`
- Role: Builder classes defining how clusters are combined or approximated when generating HLOD actors.
- Key behaviors: configure merge/simplify parameters, use instancing or custom actor types for cluster output.

### `HLODModifierMeshDestruction`
- Role: Modifier that applies mesh destruction rules to generated HLOD assets.

## 5. Typical usage patterns
- Enabled automatically in editor builds; used when generating HLOD data for World Partition maps.
- Choose desired HLOD builder type for layers to control merge/simplify/instance strategies.
- Apply the mesh destruction modifier if fractured/destruction-ready HLOD meshes are required.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

