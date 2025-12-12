# Skeletal Mesh Editing Tools Plugin Overview

## 1. What this plugin does
- Adds modeling tools specialized for skeletal meshes (creating skeletons, painting skin weights, editing mesh data).
- Provides an editor mode with tool targets backed by skeletal-mesh-aware dynamic mesh components.
- Extends the Modeling Tools framework for workflows that require skinning data preservation.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor modeling mode and toolkit for skeletal mesh workflows exposed directly to users.

## 3. Key Modules
- **SkeletalMeshModelingTools** (Editor)  
  - Editor-only module delivering the skeletal mesh modeling mode and tool targets.  
  - Notable types: `USkeletalMeshModelingToolsEditorMode`, `USkeletalMeshModelingToolsEditorModeToolkit`, `USKMBackedDynaMeshComponent`, `USKMBackedDynaMeshComponentToolTarget`, `ISKMBackedDynaMeshComponentProvider`.

## 4. Important Types & APIs

### `USkeletalMeshModelingToolsEditorMode`
- Role: Editor mode that hosts skeletal mesh modeling tools; integrates with toolkit UI (`USkeletalMeshModelingToolsEditorModeToolkit`).

### `USKMBackedDynaMeshComponent`
- Role: Dynamic-mesh component that preserves skeletal mesh attributes (weights, bones) while exposing modeling operations.

### `USKMBackedDynaMeshComponentToolTarget` / `ISKMBackedDynaMeshComponentProvider`
- Role: Tool target/provider allowing modeling tools to operate on `USKMBackedDynaMeshComponent` instances while maintaining skeletal data.

## 5. Typical usage patterns
- Enable the plugin (Animation category). Enter the Skeletal Mesh Modeling editor mode to access the skeletal-specific modeling tools.
- Select a skeletal mesh asset/actor; the mode swaps in `USKMBackedDynaMeshComponent` to edit geometry while keeping skin weights and bone data intact.
- Use the toolkit UI to run modeling operations (painting weights, mesh sculpting, skeleton edits) and then commit changes back to the skeletal mesh.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
