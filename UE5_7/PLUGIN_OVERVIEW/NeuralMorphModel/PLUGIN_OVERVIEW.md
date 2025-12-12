# ML Deformer Neural Morph Model Plugin Overview

## 1. What this plugin does
- Supplies a neural morph-based model implementation for the ML Deformer Framework.
- Uses trained morph targets driven by a neural network to enhance skeletal mesh deformation quality.
- Provides editor models/settings for training, visualization, and project defaults.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Chosen by artists when creating ML Deformer assets (`UNeuralMorphModel`/`UNeuralMorphModelVizSettings`) and configured in the deformer editor for training/runtime deformation.

## 3. Key Modules
- **NeuralMorphModel** (Runtime)  
  - Runtime neural morph model and visualization settings.  
  - Notable types: `UNeuralMorphModel` (extends the ML deformer model base), `UNeuralMorphModelVizSettings`.
- **NeuralMorphModelEditor** (Editor)  
  - Editor integration and project settings for the neural morph workflow.  
  - Notable types: `FNeuralMorphEditorModel`, `UNeuralMorphEditorProjectSettings`, `UNeuralMorphModelVizSettingsDetails`.

## 4. Important Types & APIs

### `UNeuralMorphModel`
- Role: ML deformer model that relies on morph targets driven by a neural network; consumed by `UMLDeformerComponent`.
- Exposes model parameters, training data references, and runtime evaluation hooks inherited from the framework.

### `UNeuralMorphModelVizSettings`
- Role: Visualization controls for the neural morph model (e.g., morph influence previews, debug overlays) used in the deformer editor.

### Editor types (`FNeuralMorphEditorModel`, `UNeuralMorphEditorProjectSettings`)
- Role: Configure project-level defaults for neural morph training/inference and provide editor-side preview logic.

## 5. Typical usage patterns
- Enable along with `MLDeformerFramework`; create an ML Deformer asset selecting the Neural Morph model.
- Train the model with appropriate morph targets/inputs; adjust visualization using `UNeuralMorphModelVizSettings` in the deformer editor.
- At runtime, attach `UMLDeformerComponent` to a skeletal mesh and assign the neural morph deformer asset; drive blend weight via `SetWeight`.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

