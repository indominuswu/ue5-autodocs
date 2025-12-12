# Experimental Mesh Modeling Toolset Plugin Overview

## 1. What this plugin does
- Experimental extensions to the core modeling toolset, adding additional mesh baking, alignment, pivot, and grid-based tools.
- Provides supplementary UI modules for modeling panels and adapters for experimental geometry processing.
- Builds on the Interactive Tools Framework; intended for previewing in-progress modeling features.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Modeling mode UI for experimental tools plus runtime tool implementations.

## 3. Key Modules
- **MeshModelingToolsExp** (Runtime)
  - Role: Experimental tools for baking mesh attributes, cube/grid modeling, alignment, pivot edits, and normals editing.
  - Notable tools: `UAlignObjectsTool`, `UBakeMeshAttributeMapsTool`, `UBakeMultiMeshAttributeMapsTool`, `UCubeGridTool`, `UDrawPolyPathTool`, `UEditNormalsTool`, `UEditPivotTool`, `UAddPatchTool`, `UBakeTransformTool`.
- **MeshModelingToolsEditorOnlyExp** (Editor)
  - Role: Editor integration for the experimental tools.
- **GeometryProcessingAdapters** (Editor)
  - Role: Bridges experimental geometry processing code to the tooling layer.
- **ModelingUI** (Runtime) / **ModelingEditorUI** (Editor)
  - Role: Shared UI widgets and layout helpers for the modeling panels when experimental tools are enabled.

## 4. Important Types & APIs
### Experimental tool highlights
- `UAlignObjectsTool`: Aligns selected objects using bounding boxes and transforms.
- `UBakeMeshAttributeMapsTool` / `UBakeMeshAttributeVertexTool` / `UBakeMultiMeshAttributeMapsTool`: Bakes attributes (normals, AO, curvature, custom data) from high-poly to targets.
- `UCubeGridTool`: Grid-based modeling workflow for blockouts.
- `UEditPivotTool`: Adjusts actor/mesh pivot interactively.
- `UEditNormalsTool`: Recomputes and edits vertex normals with configurable weighting.
- `UAddPatchTool` / `UBakeTransformTool` / `UDrawPolyPathTool`: Utility tools for patch creation, transform baking, and spline-like polygon drawing.

### `ModelingUI` / `ModelingEditorUI`
- Role: Provides experimental modeling panels, command bindings, and styles used to surface the above tools in the modeling mode.

## 5. Typical usage patterns
- Enable the plugin (Experimental). In the Modeling mode, enable experimental tool categories to access the added tools.
- Use baking tools to generate texture/attribute maps from high-poly meshes; export results as assets.
- Use alignment, pivot, and cube grid tools during blockout or layout workflows.
- Expect APIs and behaviors to change; validate tool outputs before production use.

## 6. Version-specific notes (UE 5.7)
- Marked Experimental in the `.uplugin`. No additional UE 5.7-specific flags observed.
