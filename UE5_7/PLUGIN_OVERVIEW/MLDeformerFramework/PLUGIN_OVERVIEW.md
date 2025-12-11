# ML Deformer Framework Plugin Overview

## 1. What this plugin does
- Provides the core machine-learning-based mesh deformation framework for skeletal meshes.
- Supports authoring ML Deformer assets and running runtime inference to improve mesh fidelity beyond skinning.
- Includes editor tooling for training data setup, visualization, and asset creation.

## 2. Key Modules
- **MLDeformerFramework** (Runtime)  
  - Runtime inference and component integration.  
  - Notable types: `UMLDeformerComponent`, `UMLDeformerModelInstance`, `UMLDeformerAsset`, visualization settings (`UMLDeformerVizSettings`, `UMLDeformerGeomCacheVizSettings`, `UMLDeformerMorphModelVizSettings`), `UMLDeformerTrainingDataProcessorSettings`.
- **MLDeformerFrameworkEditor** (Editor)  
  - Asset factories and editor modes for training/preview.  
  - Notable types: `UMLDeformerAssetFactory`, `UMLDeformerEditorMode`, `UMLDeformerEditorModel`, viz settings detail customizations, training data processor settings customization.

## 3. Important Types & APIs

### `UMLDeformerComponent`
- Role: Actor component that runs ML deformer inference against a target `USkeletalMeshComponent`.
- Key properties/APIs: `SetDeformerAsset`, `SetupComponent` to bind an asset and mesh, `SetWeight`/`GetWeight` to blend deformation, `UpdateSkeletalMeshComponent`, `GetModelInstance` for runtime model access. Deprecated quality-level getters remain for compatibility.

### `UMLDeformerAsset` / `UMLDeformerModelInstance`
- Role: Asset holds trained model data; model instance executes inference and feeds deformation back to the mesh.

### `UMLDeformerVizSettings` and derived viz settings
- Role: Configure editor/runtime visualization of deformer outputs (e.g., geometry cache/morph visualizers).

### `UMLDeformerTrainingDataProcessorSettings`
- Role: Settings object controlling preprocessing/training data steps used by the framework.

### Editor types (`UMLDeformerEditorMode`, `UMLDeformerEditorModel`, `UMLDeformerGeomCacheEditorModel`)
- Role: Editor-only views and tooling for training, previewing, and inspecting ML deformers inside their dedicated editor.

## 4. Typical usage patterns
- Enable the plugin and create an ML Deformer Asset via the Content Browser (factory supplied by the editor module).
- Train/configure the deformer in the ML Deformer editor mode; adjust viz settings to inspect geometry cache outputs or morph influences.
- Add `UMLDeformerComponent` to an actor with a compatible skeletal mesh; call `SetupComponent` and adjust `Weight` to blend the ML deformation at runtime.
- Use developer settings and viz panels during PIE to profile (`GetTickPerfCounter` in editor) and validate deformation output.

## 5. Version-specific notes (UE 5.7)
- Deprecated quality-level APIs remain marked for removal (deprecated since 5.4) but still present for compatibility.
- No other explicit UE 5.7-specific notes found; overview reflects the current plugin state in the UE 5.7 source tree.
