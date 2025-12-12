# Neural Rendering Plugin Overview

## 1. What this plugin does

- Enables neural rendering features with a focus on neural post-processing pipelines.
- Provides a lightweight module that can be extended to host neural render passes.

## 2. Editor/Runtime surfaces

- User-facing: No - Only a stub `NeuralPostProcessing` module/`FNeuralPostProcessingModule` without built-in passes, assets, or editor/UI surfaces for users.

## 3. Key Modules

- **NeuralPostProcessing** (RuntimeAndProgram) – Module shell for neural post-processing support.

## 4. Important Types & APIs

### `FNeuralPostProcessingModule`

- `IModuleInterface` implementation that initializes/shuts down neural post-processing facilities; serves as the extension point for neural render passes.

## 5. Typical usage patterns

- Enable the plugin when experimenting with neural post-processing; extend the module to register render passes or integrate with rendering pipelines.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific details present in the module.

