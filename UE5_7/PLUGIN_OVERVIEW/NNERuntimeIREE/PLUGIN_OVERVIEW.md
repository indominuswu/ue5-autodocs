# NNERuntimeIREE Plugin Overview

## 1. What this plugin does

- Supplies an IREE/MLIR/LLVM-based runtime for the Neural Network Engine (NNE), compiling neural networks to optimized game-ready code.
- Provides editor support for importing IREE-compatible model data.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Provides the IREE execution provider plus `UNNERuntimeIREEModelDataFactory` so developers can import and run NNE models through the IREE backend.

## 3. Key Modules

- **IREEUtils**, **IREEDriverRDG** (Runtime) – IREE utility code and RDG driver integration.
- **NNERuntimeIREE** (Runtime) – Core runtime implementation.
- **NNERuntimeIREEShader** (Runtime) – Shader pieces for IREE execution paths.
- **NNERuntimeIREEEditor** (Editor) – Model data factory/editor integration.

## 4. Important Types & APIs

### `UNNERuntimeIREEModelDataFactory`

- `UFactory` subclass that imports model binaries for IREE execution (`FactoryCreateBinary`, `FactoryCanImport`).

### Runtime classes (internal)

- Internal headers (`NNERuntimeIREE.h`, driver modules) manage compilation/execution pipelines; exposed via module services rather than public UObjects.

## 5. Typical usage patterns

- Import an NNE model with `UNNERuntimeIREEModelDataFactory`, then execute it through NNE APIs using the IREE runtime for performance-focused builds.
- Use the runtime modules when targeting platforms where IREE’s compiled pipelines are desired.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-only notes; reflects the current runtime/editor code.

