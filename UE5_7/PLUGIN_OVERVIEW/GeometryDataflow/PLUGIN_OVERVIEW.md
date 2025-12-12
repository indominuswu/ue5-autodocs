# Geometry Dataflow Nodes Plugin Overview

## 1. What this plugin does

- Provides a small set of Dataflow nodes focused on geometry boolean operations.
- Extends the Dataflow graph system with mesh processing nodes that can be composed in editors or tools relying on Dataflow.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Adds geometry boolean nodes that users drop into Dataflow graphs when building geometry/Fracture workflows.

## 3. Key Modules

- **GeometryDataflowNodes** (Runtime)  
  - Role: Registers geometry-oriented Dataflow nodes.  
  - Notable types: `GeometryDataflowNodesPlugin`, `MeshBooleanNodes`.

## 4. Important Types & APIs

### `MeshBooleanNodes`

- Role: Defines Dataflow nodes for boolean operations on mesh inputs (union/difference/intersection utilities).
- Key inputs: Mesh operands, operation type, tolerance parameters (per the node definitions).

### `GeometryDataflowNodesPlugin`

- Role: Module entry point that registers the nodes with the Dataflow subsystem.

## 5. Typical usage patterns

- Enable the plugin alongside Dataflow; in a Dataflow graph, add the mesh boolean nodes to combine or subtract mesh geometry.
- Use within tools that embed Dataflow (e.g., Geometry Collection/Fracture workflows) to add boolean processing stages.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

