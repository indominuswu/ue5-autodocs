# Geometry Script Plugin Overview

## 1. What this plugin does

- Exposes a large Blueprint-function-library surface for procedural and scripted mesh/geometry manipulation built on Dynamic Mesh.
- Covers mesh creation, boolean ops, selection, UVs, normals/tangents, baking, voxelization, collision, and point/shape utilities.
- Adds editor helpers for generating assets and dynamic mesh actors directly from Blueprint/Editor scripting.

## 2. Key Modules

- **GeometryScriptingCore** (Runtime)  
  - Role: Core Blueprint libraries for geometry operations.  
  - Notable types: Function libraries such as `UGeometryScriptLibrary_CollisionFunctions`, `UGeometryScriptLibrary_MeshAssetFunctions`, `UGeometryScriptLibrary_MeshBakeFunctions`, `UGeometryScriptLibrary_MeshBooleanFunctions`, `UGeometryScriptLibrary_MeshNormalsFunctions`, `UGeometryScriptLibrary_MeshRemeshFunctions`, `UGeometryScriptLibrary_MeshUVFunctions`, `UGeometryScriptLibrary_MeshSelectionFunctions`, `UGeometryScriptLibrary_MeshSamplingFunctions`, `UGeometryScriptLibrary_PointSetFunctions`, `UGeometryScriptLibrary_ShapeFunctions`, `UGeometryScriptLibrary_VectorMathFunctions`, `UGeometryScriptLibrary_VolumeTextureBakeFunctions`, plus shared types (`FGeometryScriptMeshSelection`, `FGeometryScriptTriangleList`, `FGeometryScriptPolyPath`) and debug helpers.

- **GeometryScriptingEditor** (Editor)  
  - Role: Editor-facing utilities for asset creation and dynamic mesh actor support.  
  - Notable types: `UEditorGeometryGenerationSubsystem`, `UGeneratedDynamicMeshActor`, `UGeometryScriptLibrary_CreateNewAssetUtilityFunctions`, `UGeometryScriptLibrary_EditorDynamicMeshUtilityFunctions`, `UGeometryScriptLibrary_OpenSubdivUtilityFunctions`, `UGeometryScriptLibrary_EditorTextureMapFunctions`.

## 3. Important Types & APIs

### Blueprint function libraries (`UGeometryScriptLibrary_*`)

- Role: Static Blueprint-callable functions that operate on `UDynamicMesh`, `UStaticMesh`, `USkeletalMesh`, and auxiliary data types.
- Key areas: mesh primitives/creation, booleans, deform/edit, bone weight transfer, normals/tangents, UV generation, polygroup operations, sampling/baking, voxelization, collision generation, list/math utilities, and volume/texture baking.
- Most functions accept `UGeometryScriptDebug*` optional parameters for logging/line drawing.

### `UEditorGeometryGenerationSubsystem` / `UGeneratedDynamicMeshActor`

- Role: Editor subsystem and actor to spawn/manage dynamic mesh assets directly in editor scenes via Blueprint.
- Key functions: Create dynamic mesh actors, convert/generate assets, run geometry script operations in-editor.

### Asset/texture utility libraries (Editor)

- Role: Helpers to create new meshes/material assets, generate texture maps, and interface with OpenSubdiv in editor workflows.

## 4. Typical usage patterns

- Enable the plugin, then in Blueprint (or Python via Blueprint-callable functions) use `UGeometryScriptLibrary_*` nodes to generate or modify meshes at runtime or in editor utility widgets.
- Operate on `UDynamicMesh` instances for intermediate processing; convert to `UStaticMesh`/`USkeletalMesh` with asset utility functions when ready to save.
- In editor scripts, use `UEditorGeometryGenerationSubsystem` and `UGeneratedDynamicMeshActor` to create preview actors, then run geometry script nodes to procedurally build/alter geometry.
- Use collision/voxel/selection helpers to prepare meshes for simulation or further modeling steps.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
