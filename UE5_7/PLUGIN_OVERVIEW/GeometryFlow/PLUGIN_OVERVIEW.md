# GeometryFlow Plugin Overview

## 1. What this plugin does

- Introduces a GeometryFlow graph framework for building reusable geometry-processing pipelines as node graphs.
- Supplies core node types (math, switching, data transfer) plus a large library of mesh-processing nodes (simplify, normals/UVs, baking, collision) built on Dynamic Mesh utilities.
- Adds editor-facing node registrations for convenience nodes such as automatic UV generation.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Developers build GeometryFlow graphs with mesh-processing nodes (simplify, auto-UV, bake, collision) and use editor-registered nodes for tooling workflows.

## 3. Key Modules

- **GeometryFlowCore** (Runtime)  
  - Role: Core graph runtime, node registration, data containers, and generic nodes.  
  - Notable types: `FGeometryFlowGraph`, `FGeometryFlowNode`, `FGeometryFlowNodeFactory`, `FGeometryFlowGraphUtil`, `FGeometryFlowImmutableData`, `FGeometryFlowMovableData`, base nodes like `FBinaryOpLambdaNode`, `FSwitchNode`, `FTransferNode`, `FTransformerWithSettingsNode`, `FGeometryFlowTSourceNode`.

- **GeometryFlowMeshProcessing** (Runtime)  
  - Role: Mesh-processing node suite and data types built on Dynamic Mesh.  
  - Notable types: data structs (`FDynamicMeshData`, `FCollisionGeometryData`, `FMeshImageBakingData`, `FWeightMapData`), nodes such as `MeshSimplifyNode`, `MeshRepackUVsNode`, `MeshNormalFlowNode`, `MeshThickenNode`, `MeshVoxMorphologyNode`, `GenerateSimpleCollisionNode`, `BakeMeshNormalMapNode`, `MeshAutoGenerateUVsNode` registration.

- **GeometryFlowMeshProcessingEditor** (Editor)  
  - Role: Editor module that registers editor-only mesh processing nodes/utilities (e.g., auto UV generation UI hooks).  
  - Notable types: `FGeometryFlowMeshProcessingEditorModule`, `MeshProcessingEditorNodeRegistration`.

## 4. Important Types & APIs

### `FGeometryFlowGraph` / `FGeometryFlowNode`

- Role: Represent a directed graph of processing nodes; nodes pass typed `Immutable`/`Movable` geometry data between steps.
- Key functions: Add nodes, connect pins, evaluate graph, register node factories.

### Mesh processing nodes

- Role: Operations for simplifying, remeshing, recomputing normals/tangents, solidifying, voxel morphology, UV repacking, collision generation, and mesh baking tasks.
- Key inputs: `FDynamicMeshData` plus per-node settings structs; outputs new mesh/attribute data for downstream nodes.

### Data containers (`FDynamicMeshData`, `FCollisionGeometryData`, etc.)

- Role: Structured payloads for mesh geometry, collision primitives, index sets, baked images, and weight maps that flow between nodes.

## 5. Typical usage patterns

- Enable the plugin and construct a `FGeometryFlowGraph` at runtime or in tooling, registering nodes from `GeometryFlowCore` and `GeometryFlowMeshProcessing`.
- Compose graphs that ingest a dynamic mesh, run processing nodes (simplify, remesh, bake textures, generate collision), and output modified mesh data.
- In the editor, leverage the mesh processing editor nodes (e.g., auto UV generation) where GeometryFlow-based tools expose them.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

