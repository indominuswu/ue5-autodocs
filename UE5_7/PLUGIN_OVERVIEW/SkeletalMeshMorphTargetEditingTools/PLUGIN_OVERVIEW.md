# Skeletal Mesh Morph Target Editing Tools Plugin Overview

## 1. What this plugin does
- Experimental editor tools for authoring and editing morph targets directly inside the Skeletal Mesh Editor.
- Provides brush-based sculpting, erase tools, and properties for morph editing workflows.
- Integrates with the Skeletal Mesh Modeling Tools stack.

## 2. Key Modules
- **SkeletalMeshMorphTargetEditingTools** (Editor)
  - Role: Registers morph sculpt/erase tools, commands, styles, and property sets for morph target editing.
  - Notable types: `MorphTargetVertexSculptTool`, `EraseMorphTargetBrushOps`, `SKMMorphTargetEditingToolsCommands`, module/stylesheet classes.

## 3. Important Types & APIs
### `UMorphTargetVertexSculptTool`
- Role: Sculpting tool to modify morph target vertex offsets directly in the editor.
- Key properties: sculpt strength/falloff, target selection via `MorphTargetEditingToolProperties`.

### `UEraseMorphTargetBrushOps`
- Role: Brush operations to erase morph deltas on selected regions.

### `USKMMorphTargetEditingToolsModule`
- Role: Module registering tools/commands and binding them to the Skeletal Mesh Editor UI.

### `IMorphTargetEditingToolInterface`
- Role: Interface allowing tools to share common behavior/contract within the editor.

## 4. Typical usage patterns
- Enable the plugin (requires SkeletalMeshModelingTools).
- Open a skeletal mesh in the Skeletal Mesh Editor; select the morph target editing tools from the toolbar.
- Use sculpt or erase brushes to adjust morph target geometry; tweak settings in the details panel.
- Save the skeletal mesh to persist updated morph targets.

## 5. Version-specific notes (UE 5.7)
- Marked experimental in the `.uplugin`.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
