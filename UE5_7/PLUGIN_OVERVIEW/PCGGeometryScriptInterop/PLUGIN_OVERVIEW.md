# Procedural Content Generation Framework (PCG) Geometry Script Interop Plugin Overview

## 1. What this plugin does
- Adds PCG nodes that operate on `UPCGDynamicMeshData` using Geometry Script utilities.
- Enables converting PCG point/static mesh inputs into dynamic meshes, performing boolean/transform operations, and exporting results.
- Provides helper components to keep dynamic mesh resources alive for preview/rendering.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Ships PCG nodes (`UPCGDynamicMesh*Settings`, boolean/transform/merge/save/spawn nodes) and managed components that authors use in PCG graphs to edit dynamic meshes via Geometry Script.

## 3. Key Modules
- **PCGGeometryScriptInterop** (Runtime)  
  - Role: Implements dynamic-mesh PCG nodes and helpers that bridge PCG data to Geometry Script pipelines.

## 4. Important Types & APIs
- `UPCGDynamicMeshBaseSettings` / `IPCGDynamicMeshBaseElement`  
  - Role: Base settings/element classes for dynamic mesh nodes; define dynamic-mesh pin types and disable caching.
- `UPCGDynamicMeshTransformSettings` / `FPCGDynamicMeshTransformElement`  
  - Role: PCG node to apply a `FTransform` to each dynamic mesh in the input.
- Other notable node settings (all under `PCGGeometryScriptInterop/Elements`):  
  - `UPCGCreateEmptyDynamicMeshSettings`: start from an empty mesh.  
  - `UPCGAppendMeshesFromPointsSettings`: build dynamic meshes from input points/mesh assets.  
  - `UPCGMeshSamplerSettings`: sample geometry from static meshes into dynamic meshes.  
  - `UPCGBooleanOperationSettings`: boolean operations between meshes.  
  - `UPCGMergeDynamicMeshesSettings`, `UPCGSaveDynamicMeshToAssetSettings`, `UPCGSpawnDynamicMeshSettings`, `UPCGGetDynamicMeshDataSettings`, `UPCGPrimitiveCrossSectionSettings`, `UPCGDynamicMeshTransformSettings`, `UPCGDynamicMeshBlueprintSettings`.  
- `UPCGDynamicMeshManagedComponent`  
  - Role: Managed component wrapper that holds dynamic mesh data alive for preview/rendering.
- `UPCGGeometryHelpers`  
  - Role: Utility helpers for converting between PCG data and Geometry Script data structures.

## 5. Typical usage patterns
- Enable alongside `PCG` and `GeometryScripting`.
- In a PCG graph, use nodes such as “Create Empty Dynamic Mesh,” “Append Meshes From Points,” or “Boolean Operation” to build/edit meshes procedurally.  
- Use “Dynamic Mesh Transform” to apply transforms per-mesh and “Save Dynamic Mesh To Asset” to bake outputs.  
- Use “Spawn Dynamic Mesh” to place generated meshes into the level with managed lifetime.

## 6. Version-specific notes (UE 5.7)
- Marked beta in the `.uplugin`.  
- No explicit UE 5.7-only code paths documented; overview reflects current 5.7 implementation.

