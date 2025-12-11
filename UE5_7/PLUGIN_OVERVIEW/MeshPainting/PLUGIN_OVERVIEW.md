# Mesh Painting Plugin Overview

## 1. What this plugin does
- Editor Mesh Paint mode for painting vertex colors or textures directly onto meshes.
- Provides tools for static meshes, skeletal meshes, spline meshes, and geometry collections via adapter interfaces.
- Includes import options, brush settings customizations, and specialized selection helpers for paint workflows.

## 2. Key Modules
- **MeshPaintEditorMode** (Editor)
  - Role: Editor mode implementation, commands, toolkit, and settings UI for Mesh Paint mode.
  - Notable types: `UMeshPaintEditorMode`, `FMeshPaintModeCommands`, `FMeshPaintModeToolkit`, `UMeshPaintModeSettings`.
- **MeshPaintingToolset** (Editor)
  - Role: Core painting tool implementations and adapters for different mesh types.
  - Notable types: `UMeshVertexPaintingTool`, `UMeshTexturePaintingTool`, `UMeshPaintComponentAdapter` (and static/skeletal/spline/geometry collection adapters), `FMeshPaintGeometryCollectionAdapter`, `UMeshPaintHelpers`, `UMeshSelect`.

## 3. Important Types & APIs
### `UMeshPaintEditorMode`
- Role: Activates Mesh Paint mode, registers commands, and hosts the brush/paint settings UI.
- Key properties: brush radius/strength, paint vs. erase, channel toggles, fill/gradient options.

### `UMeshVertexPaintingTool` / `UMeshTexturePaintingTool`
- Role: Execute vertex color painting or texture painting on the selected mesh components.
- Key properties: target mesh/component adapters, paint falloff, normal alignment, and per-channel masking.

### `UMeshPaintComponentAdapter` family
- Role: Adapter interface and implementations that expose mesh data (vertices/UVs) for painting across mesh types.
- Examples: `UMeshPaintStaticMeshAdapter`, `UMeshPaintSkeletalMeshAdapter`, `UMeshPaintSplineMeshAdapter`, `FMeshPaintGeometryCollectionAdapter`.

## 4. Typical usage patterns
- Enable the plugin (Editor). Enter Mesh Paint mode from the toolbar.
- Select a mesh actor; choose Vertex or Texture painting. Adjust brush settings and paint directly in the viewport.
- Use adapters to paint on different component types; import/export vertex colors via the provided import options panel.
- Leverage selection helpers (`UMeshSelect`, octree support) for isolating paint regions.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; Mesh Paint mode matches the UE 5.7 implementation.
