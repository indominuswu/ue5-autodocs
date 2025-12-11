# Procedural Mesh Component Plugin Overview

## 1. What this plugin does

- Provides a runtime component for building and rendering mesh geometry entirely in code or Blueprints.
- Includes Blueprint utilities to generate mesh data (boxes, grids, slicing), copy collision, and convert static meshes.
- Useful for dynamic/interactive geometry, runtime mesh generation, or prototyping modeling workflows.

## 2. Key Modules

- **ProceduralMeshComponent** (Runtime)  
  - Role: Core component implementation and Blueprint library.
  - Notable types: `UProceduralMeshComponent`, `UKismetProceduralMeshLibrary`.
- **ProceduralMeshComponentEditor** (Editor)  
  - Role: Editor integration and validation helpers for the component.

## 3. Important Types & APIs

### `UProceduralMeshComponent`

- Role: Scene component that owns mesh sections generated at runtime.
- Key functions: `CreateMeshSection`, `UpdateMeshSection`, `ClearMeshSection`, `SetMaterial`, `AddCollisionConvexMesh`.
- Key properties: `bUseComplexAsSimpleCollision`, section visibility, per-section collision flags.

### `UKismetProceduralMeshLibrary`

- Role: BlueprintFunctionLibrary with helpers to generate common geometry.
- Key functions: `CreateGridMeshWelded`, `CreateGridMeshTriangles`, `CreateBoxMesh`, `SliceProceduralMesh`, `CopyProceduralMeshFromStaticMeshComponent`.

## 4. Typical usage patterns

- Add a `UProceduralMeshComponent` to an actor (or derive from `AProceduralMeshActor`) and generate sections at runtime in C++ or Blueprints.
- Use `UKismetProceduralMeshLibrary` nodes to create vertex/index/normal/UV arrays, then feed them into `CreateMeshSection`.
- For collision, call `ContainsPhysicsTriMeshData`/`AddCollisionConvexMesh` or enable complex-as-simple for fast setup.
- In editor builds, the accompanying editor module validates section data and integrates with component details panels.

## 5. Version-specific notes (UE 5.7)

- Enabled by default in UE 5.7.
- No explicit 5.7-specific changes or deprecations noted in the source.
