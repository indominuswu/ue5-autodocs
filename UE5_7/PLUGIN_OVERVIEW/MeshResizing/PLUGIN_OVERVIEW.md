# Mesh Resizing Plugin Overview

## 1. What this plugin does
- Experimental toolkit for resizing and warping meshes, including body-aware constraints and RBF-based deformation.
- Provides runtime core math (constraints, interpolation), dataflow nodes, and editor tools for landmark-driven mesh wrapping.
- Integrates with Dataflow graphs to automate resizing operations.

## 2. Key Modules
- **MeshResizingCore** (Runtime)
  - Role: Core algorithms and data structures for mesh resizing (constraints, RBF interpolation, region resizing).
  - Notable types: `FCustomRegionResizing`, `FMesh3DConstraints`, `FRBFInterpolation`, `FBaseBodyTools`.
- **MeshResizingNodes** (Runtime)
  - Role: Dataflow nodes that expose resizing operations to graphs.
  - Notable nodes/types: `FMeshWrapNode`, `FMeshWarpNode`, `FMeshResizingTextureNodes`, `FMeshConstraintNodes`, `FRBFInterpolationNodes`, `FAlignUVMeshNode`, `FUVMeshTransformNode`, `FUVResizeControllerNode`.
- **MeshResizingEditorTools** (Editor)
  - Role: Editor tools and command bindings for interactive mesh wrap landmark selection and tool actions.
  - Notable types: `UMeshWrapLandmarkSelectionTool`, `FMeshResizingToolActionCommandBindings`.
- **MeshResizingEngine** (Runtime)
  - Role: Engine integration scaffolding for resizing features (no public headers).

## 3. Important Types & APIs
### `FCustomRegionResizing` / `FMesh3DConstraints`
- Role: Define constraint sets and region rules that drive how vertices are repositioned during resizing.

### Dataflow nodes (from `MeshResizingNodes`)
- Role: Nodes such as `FMeshWrapNode` and `FMeshWarpNode` wrap/warp meshes against targets; UV nodes adjust and align UV layouts; RBF nodes drive smooth deformation weights.

### `UMeshWrapLandmarkSelectionTool`
- Role: Editor tool for selecting landmarks on meshes to guide wrap/resize operations.

## 4. Typical usage patterns
- Enable the experimental plugin. Build a Dataflow graph using Mesh Resizing nodes to define warp/resize logic.
- Use `UMeshWrapLandmarkSelectionTool` to author landmark sets, then run the graph to drive resizing with constraints and RBF interpolation.
- Combine UV nodes to realign textures after geometric changes.

## 5. Version-specific notes (UE 5.7)
- Marked as experimental and disabled by default. No additional UE 5.7-specific notes found.
