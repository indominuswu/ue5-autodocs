# NNERuntimeIREE Plugin Overview

## 1. What this plugin does

- Supplies an IREE/MLIR/LLVM-based runtime for the Neural Network Engine (NNE), compiling neural networks to optimized game-ready code.
- Provides editor support for importing IREE-compatible model data.

## 2. Key Modules

- **IREEUtils**, **IREEDriverRDG** (Runtime) – IREE utility code and RDG driver integration.
- **NNERuntimeIREE** (Runtime) – Core runtime implementation.
- **NNERuntimeIREEShader** (Runtime) – Shader pieces for IREE execution paths.
- **NNERuntimeIREEEditor** (Editor) – Model data factory/editor integration.

## 3. Important Types & APIs

### `UNNERuntimeIREEModelDataFactory`

- `UFactory` subclass that imports model binaries for IREE execution (`FactoryCreateBinary`, `FactoryCanImport`).

### Runtime classes (internal)

- Internal headers (`NNERuntimeIREE.h`, driver modules) manage compilation/execution pipelines; exposed via module services rather than public UObjects.

## 4. Typical usage patterns

- Import an NNE model with `UNNERuntimeIREEModelDataFactory`, then execute it through NNE APIs using the IREE runtime for performance-focused builds.
- Use the runtime modules when targeting platforms where IREE’s compiled pipelines are desired.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-only notes; reflects the current runtime/editor code.

