# Skeletal Mesh Simplifier (Early Access) Plugin Overview

## 1. What this plugin does

- Implements a skeletal mesh reduction pipeline for generating LODs on deforming meshes.
- Uses quadric-error simplification utilities tailored for skinned meshes.

## 2. Key Modules

- **SkeletalMeshReduction** (Editor, Default)  
  - Role: Provides the skeletal mesh reduction implementation used by the editor when building LODs.

## 3. Important Types & APIs

### `ISkeletalMeshReduction`

- Role: Interface exposed by the module to drive LOD generation for skeletal meshes.

### Simplifier internals

- Quadric-based reducers and helpers (`FSkeletalSimplifier`, `FSkeletalSimplifierMeshManager`, `FSkeletalSimplifierQuadrics`, `FSkeletalMeshReductionSkinnedMesh`) that perform the actual simplification math and mesh management.

## 4. Typical usage patterns

- Enable the plugin in the editor to make the early-access skeletal reduction backend available for LOD generation.
- Trigger LOD build/reduction for skeletal meshes through the standard mesh editor; the plugin’s reducer will handle quadric-based simplification.

## 5. Version-specific notes (UE 5.7)

- Marked Early Access in the `.uplugin`; no additional UE 5.7-specific notes found.
