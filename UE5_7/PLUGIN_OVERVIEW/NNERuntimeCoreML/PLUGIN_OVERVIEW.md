# NNERuntimeCoreML Plugin Overview

## 1. What this plugin does

- Provides a CoreML-backed runtime for the Neural Network Engine (NNE) on Apple platforms.
- Includes an editor factory for importing model data in a CoreML-compatible format.

## 2. Key Modules

- **NNERuntimeCoreML** (RuntimeAndProgram) – CoreML runtime implementation and helpers.
- **NNERuntimeCoreMLEditor** (Editor) – Model data factory and editor integration.

## 3. Important Types & APIs

### `UNNERuntimeCoreMLModelDataFactory`

- `UFactory` subclass that imports model binaries for use with the CoreML runtime (`FactoryCreateBinary`, `FactoryCanImport`).

### Runtime classes (internal)

- Runtime headers (`NNERuntimeCoreML.h`, `NNERuntimeCoreMLModel.h`, `NNERuntimeCoreMLNPUHelper`) implement execution and NPU helper logic; exposed through the module rather than public UObject types.

## 4. Typical usage patterns

- Enable the plugin on Apple platforms, import models via `UNNERuntimeCoreMLModelDataFactory`, and run them through NNE APIs with the CoreML execution provider.
- Use the editor module to create CoreML-backed `UNNEModelData` assets that can be referenced by inference code.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific notes observed; overview reflects the current runtime/editor setup.

