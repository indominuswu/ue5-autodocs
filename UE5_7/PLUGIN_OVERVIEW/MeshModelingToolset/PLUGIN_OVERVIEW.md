# Mesh Modeling Toolset Plugin Overview

## 1. What this plugin does
- Core modeling suite built on the Interactive Tools Framework for creating, editing, and sculpting meshes in-editor and at runtime.
- Provides dozens of mesh creation/deformation/boolean/painting tools plus supporting components, operators, and utility APIs.
- Supplies editor-only integrations (UI, details, operators) and runtime modules for tool execution and previewing.
- Forms the foundation for the Modeling mode/tool palette and other modeling plugins.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Modeling mode/tool palette UI plus runtime tools/components for mesh editing and scripting.

## 3. Key Modules
- **MeshModelingTools** (Runtime)
  - Role: Implements mesh tools for sculpting, painting, booleans, remeshing, deformation, primitive creation, and mesh processing.
  - Notable tools: `UAddPrimitiveTool`, `UDynamicMeshSculptTool`, `UEditMeshPolygonsTool`, `UMeshVertexPaintTool`, `UCSGMeshesTool`, `UDisplaceMeshTool`, `UMeshAttributePaintTool`, `ULatticeDeformerTool`.
- **MeshModelingToolsEditorOnly** (Editor)
  - Role: Editor integration for the runtime tools (UI registration, tool factories, asset interactions).
- **ModelingComponents** (Runtime)
  - Role: Shared components and utilities for modeling tools (preview meshes, `UMeshOpPreviewWithBackgroundCompute`, `UModelingObjectsCreationAPI`, `UToolSceneQueriesUtil`, `UModelingComponentsSettings`).
- **ModelingComponentsEditorOnly** (Editor)
  - Role: Editor-only extensions for modeling components and customization hooks.
- **ModelingOperators** (Runtime) / **ModelingOperatorsEditorOnly** (Editor)
  - Role: Computational operators used by tools for mesh generation, transforms, and analysis.
- **SkeletalMeshModifiers** (Editor)
  - Role: Editor utilities for applying modeling-style modifiers to skeletal meshes.

## 4. Important Types & APIs
### Representative modeling tools (from `MeshModelingTools`)
- `UAddPrimitiveTool` (quickly create primitives), `UDynamicMeshSculptTool` / `UMeshVertexSculptTool` (brush-based sculpting), `UEditMeshPolygonsTool` (poly editing), `UMeshVertexPaintTool` / `UMeshGroupPaintTool` (vertex/group painting), `UCSGMeshesTool` / `UCombineMeshesTool` (boolean/combine), `UDisplaceMeshTool` / `USpaceDeformerTool` variants (deformations), `UHoleFillTool` and `UConvertToPolygonsTool` (repair/convert), `UMeshAttributePaintTool` (attribute/UV/weights painting).

### `UModelingObjectsCreationAPI` / `UMeshOpPreviewWithBackgroundCompute`
- Role: APIs to create new assets/actors from tool outputs and to run background mesh computations with real-time previews.
- Key properties: preview materials, dynamic mesh targets, transactional support for undo/redo.

### `UModelingComponentsSettings`
- Role: Project/editor settings controlling default materials, preview behaviors, and asset creation targets for modeling tools.

## 5. Typical usage patterns
- Enable the plugin (often alongside `ModelingToolsEditorMode`). Open the Modeling mode/tool palette to access tools.
- Select meshes or start from an empty scene; run tools such as Sculpt, Poly Edit, Add Primitive, Remesh, Paint, or Booleans.
- Use tool property panels to configure output (new asset vs. modify in-place), preview materials, and target actors/components.
- For scripting/extensibility, use ModelingComponents APIs to spawn tools, feed meshes, and collect generated assets programmatically.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; overview reflects the toolset present in UE 5.7.
