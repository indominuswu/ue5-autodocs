# Skeletal Mesh Simplifier (Early Access) Plugin Overview

## 1. What this plugin does

- Implements a skeletal mesh reduction pipeline for generating LODs on deforming meshes.
- Uses quadric-error simplification utilities tailored for skinned meshes.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Provides the skeletal mesh reduction backend (`ISkeletalMeshReduction`) used by the editor when users build LODs for skinned meshes.

## 3. Key Modules

- **SkeletalMeshReduction** (Editor, Default)  
  - Role: Provides the skeletal mesh reduction implementation used by the editor when building LODs.

## 4. Important Types & APIs

### `ISkeletalMeshReduction`

- Role: Interface exposed by the module to drive LOD generation for skeletal meshes.

### Simplifier internals

- Quadric-based reducers and helpers (`FSkeletalSimplifier`, `FSkeletalSimplifierMeshManager`, `FSkeletalSimplifierQuadrics`, `FSkeletalMeshReductionSkinnedMesh`) that perform the actual simplification math and mesh management.

## 5. Typical usage patterns

- Enable the plugin in the editor to make the early-access skeletal reduction backend available for LOD generation.
- Trigger LOD build/reduction for skeletal meshes through the standard mesh editor; the plugin’s reducer will handle quadric-based simplification.

## 6. Version-specific notes (UE 5.7)

- Marked Early Access in the `.uplugin`; no additional UE 5.7-specific notes found.

