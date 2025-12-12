# ML Deformer Vertex Delta Model Plugin Overview

## 1. What this plugin does
- Implements a vertex-delta-based ML deformer model for the ML Deformer Framework.
- Drives per-vertex offsets learned during training to improve deformation fidelity on skeletal meshes.
- Ships with editor integration and visualization controls specific to the vertex-delta workflow.

## 2. Editor/Runtime surfaces

- User-facing: Yes - ML Deformer model option (`UVertexDeltaModel`/`Instance`, viz settings/editor model) that artists select and train for vertex-delta deformation.

## 3. Key Modules
- **VertexDeltaModel** (Runtime)  
  - Runtime vertex-delta model classes and viz settings.  
  - Notable types: `UVertexDeltaModel`, `UVertexDeltaModelInstance`, `UVertexDeltaModelVizSettings`.
- **VertexDeltaModelEditor** (Editor)  
  - Editor models and detail panels for authoring vertex-delta deformers.  
  - Notable types: `UVertexDeltaEditorModel`, `UVertexDeltaModelVizSettingsDetails`.

## 4. Important Types & APIs

### `UVertexDeltaModel` / `UVertexDeltaModelInstance`
- Role: ML deformer model that outputs vertex deltas; instance executes runtime inference for `UMLDeformerComponent`.
- Holds training data references and model parameters needed by the framework.

### `UVertexDeltaModelVizSettings`
- Role: Visualization settings for inspecting vertex-delta outputs (debug draws, preview toggles) within the deformer editor.

### Editor helpers (`UVertexDeltaEditorModel`, viz detail customizations)
- Role: Provide editor-side preview, tuning, and detail customization for vertex-delta assets.

## 5. Typical usage patterns
- Enable together with `MLDeformerFramework`; create a deformer asset choosing the Vertex Delta model.
- Train/configure the model in the ML Deformer editor and adjust visualization through `UVertexDeltaModelVizSettings`.
- At runtime, place `UMLDeformerComponent` on a compatible skeletal mesh, assign the vertex-delta deformer asset, and control blend weight via `SetWeight`.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

