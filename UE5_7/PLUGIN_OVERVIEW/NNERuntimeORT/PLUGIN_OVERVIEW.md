# NNERuntimeORT Plugin Overview

## 1. What this plugin does

- Provides an ONNX Runtime (ORT) backend for the Neural Network Engine (NNE), supporting CPU and DirectML execution providers.
- Focused on runtime/program builds for inference using ONNX models.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Developers target this backend when running ONNX-based `UNNEModelData` through NNE, configuring execution provider/settings for their projects.

## 3. Key Modules

- **NNERuntimeORT** (RuntimeAndProgram) – ORT runtime wrapper, model loading, settings, and tensor utilities.

## 4. Important Types & APIs

- Runtime classes (`NNERuntimeORT`, `NNERuntimeORTModel`, `NNERuntimeORTSettings`, `NNERuntimeORTTensor`) are implemented in the module for loading/executing ONNX models; they are internal but expose configuration through module settings.

## 5. Typical usage patterns

- Enable the plugin, import ONNX-backed `UNNEModelData` assets, and execute them via NNE APIs with the ORT backend (CPU or DirectML as configured).
- Adjust runtime settings (execution provider, environment options) through the module settings to match platform performance targets.

## 6. Version-specific notes (UE 5.7)

- No UE 5.7-specific notes identified; overview matches the current runtime implementation.

