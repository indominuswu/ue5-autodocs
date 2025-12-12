# NNERuntimeRDG Plugin Overview

## 1. What this plugin does
- Implements the Neural Network Engine (NNE) runtime using the Render Dependency Graph for GPU execution.
- Provides an HLSL compute shader operator library (convolution, pooling, reduction, gather/slice, element-wise ops).
- Ships RDG tensor/model infrastructure plus ONNX/protobuf tooling and model optimizer helpers for editor/program flows.
- Experimental ML plugin targeting Win64/Linux/Mac RDG-based inference.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Developers opt into this backend when running NNE inference on GPU/RDG, using its operator/tensor APIs and model builder utilities for ONNX conversion.

## 3. Key Modules
- **NNEHlslShaders** (RuntimeAndProgram): HLSL compute shader kernels for common neural network operators.
- **NNERuntimeRDG** (RuntimeAndProgram): RDG-backed NNE runtime handling tensors, operator helpers, and model execution.
- **NNERuntimeRDGData** (RuntimeAndProgram): Attribute/tensor data definitions, formats, and value traits shared by the runtime.
- **NNERuntimeRDGUtils** (EditorAndProgram): Model builder/optimizer utilities (e.g., ONNX graph handling, NNE conversions) for tooling.

## 4. Important Types & APIs
### `FNNERuntimeRDGBase`, `FNNERuntimeRDGModel`, `FNNERuntimeRDGTensor`
- Role: Core RDG runtime scaffolding for compiling models, managing tensor views, and scheduling inference passes.
- Key functions: operator registration, RDG graph construction, tensor shape helpers.
### `FNNEHlslShaders*` family
- Role: Per-operator compute shader definitions (convolution, transpose, normalization, pooling, softmax, gather/scatter, etc.).
- Key properties: operator parameter structs, shader dispatch metadata, RDG resource bindings.
### `FNNERuntimeRDGUtilsModelBuilder` / `FNNERuntimeRDGUtilsModelOptimizer*`
- Role: Helper utilities to assemble models, perform optimizer passes, and translate ONNX graphs into RDG-ready workloads.

## 5. Typical usage patterns
- Enable the experimental runtime and select the RDG backend when configuring NNE for inference on supported platforms.
- Import/build ONNX models, create RDG tensors/models, and dispatch inference; operators map to the provided HLSL shader set.
- Use the utils module inside editor/program tools to optimize or convert models before runtime execution.

## 6. Version-specific notes (UE 5.7)
- Marked as experimental in the 5.7 source tree; no additional UE 5.7-specific notes found.

