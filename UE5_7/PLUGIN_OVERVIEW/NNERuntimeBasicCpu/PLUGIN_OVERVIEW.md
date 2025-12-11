# NNERuntimeBasicCpu Plugin Overview

## 1. What this plugin does

- Implements a performant, cross-platform CPU runtime for the Neural Network Engine (NNE) targeting basic models.
- Includes a model builder API to construct and serialize models for the Basic CPU runtime.

## 2. Key Modules

- **NNERuntimeBasicCpu** (RuntimeAndProgram) – Basic CPU runtime and model builder utilities.

## 3. Important Types & APIs

### `UE::NNE::RuntimeBasic::FModelBuilder`

- In-memory model construction utility that can serialize to `FSharedBuffer` for NNE consumption.
- Provides enums for activation (`EActivationFunction`), linear layer type, weight initialization, and padding mode; supports adding layers and controlling input/output sizes.

### `UE::NNE::RuntimeBasic::FModelBuilderElement`

- Represents a constructed model element/layer with accessors for input/output sizes; used when assembling models with `FModelBuilder`.

## 4. Typical usage patterns

- Use `FModelBuilder` in tooling or preprocessing steps to generate Basic CPU-compatible model blobs, then load them via NNE runtime APIs.
- Choose activation/weight initialization options via the provided enums; ensure buffer lifetime matches builder usage when passing custom views.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific notes found; functionality reflects the current runtime builder implementation.

