# UVEditor Plugin Overview

## 1. What this plugin does
- Provides an editor for inspecting and modifying mesh UV mapping (both 2D and 3D viewports).
- Builds on the Modeling tools stack to offer UV actions, property sets, and gizmos.
- Includes tooling modules for UV editing workflows and editor-only helpers.
- Beta and enabled by default in the editor.

## 2. Key Modules
- **UVEditor** (Editor)
  - Role: Core editor mode/viewports, UX property sets, and actions (e.g., `UVEditor3DViewportMode`, `UVEditorUXPropertySets`).
- **UVEditorTools** (Editor)
  - Role: Tool implementations and operations for UV manipulation and unwrapping.
- **UVEditorToolsEditorOnly** (Editor)
  - Role: Editor-only wiring, registration, and utilities for the UV tools.

## 3. Important Types & APIs
### `SUVEditor2DViewport` / `SUVEditor3DViewport`
- Role: Slate viewports providing 2D and 3D views of UVs and the source mesh.

### `UVEditor3DViewportMode`
- Role: Editor viewport mode handling input and selection while working in the UV editor.

### `UVEditorUXPropertySets`
- Role: Collections of property sets exposed to the details panel to configure UV tools and actions.

### `UnsetUVsAction`
- Role: Editor action for clearing/unsetting UVs on selected meshes or channels.

## 4. Typical usage patterns
- Enable “UVEditor” (and Modeling tools dependencies) in the editor.
- Open a static mesh and launch the UV Editor; use the 2D/3D viewports to inspect seams and shells.
- Adjust properties via the UV editor details panel; run actions such as unsetting UVs or tool-specific operations from toolbars.
- Save changes back to the mesh asset once UV edits are finalized.

## 5. Version-specific notes (UE 5.7)
- Marked beta in the `.uplugin`.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
