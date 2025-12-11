# Compute Framework Plugin Overview

## 1. What this plugin does
- Provides authoring and runtime execution of GPU compute graphs and kernels.
- Supplies a graph asset, data interfaces/providers, and shader compilation infrastructure for user-authored compute work.
- Editor support for creating compute graph assets from text and managing compilation.

## 2. Key Modules
- **ComputeFramework** (Runtime)  
  - Role: Core compute graph types, kernel definitions, data interfaces/providers, graph instances, and dispatch runtime.
- **ComputeFrameworkEditor** (Editor)  
  - Role: Asset actions/factories for compute graphs-from-text and an editor tick to drive shader compilation.

## 3. Important Types & APIs

### Graph and execution
- `UComputeGraph`, `UComputeGraphComponent`, `FComputeGraphInstance`: Define a compute graph asset and runtime instance that dispatches kernels.
- `UComputeKernel`, `FComputeKernelPermutationSet`/`Vector`, `FComputeKernelShaderMap`: Kernel definition, permutation handling, and compiled shader maps.
- `FComputeGraphWorker`, `FComputeKernelShaderCompilationManager`: Runtime worker and shader compilation manager for kernels.

### Data interfaces/providers
- `UComputeDataInterface`, `UComputeDataProvider`: Base interfaces for exposing resources (buffers, parameters) to kernels.
- Built-in data interface implementations (e.g., buffer dispatch) live under `ComputeFramework/Private/ComputeFramework`.

### Utilities and metadata
- `UComputeGraphFromText`: Asset type that generates graphs from textual descriptions.
- `FComputeMetadataBuilder`, `FShaderParamTypeDefinition`, `FShaderParameterMetadataAllocation`: Helpers for building shader parameter metadata used by kernels.

## 4. Typical usage patterns
- Editor: Create a Compute Graph (or Compute Graph From Text) asset; define kernels and data interfaces. The editor module handles asset creation and tracks shader compilation.
- Runtime: Add a `UComputeGraphComponent` to an actor or drive a `UComputeGraph` asset directly, provide data providers/interfaces, and let the framework dispatch kernels each frame or on demand.
- Integration: Use kernel permutations and data providers to adapt kernels to different resource configurations without rewriting shaders.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific flags found; functionality reflects current runtime/editor sources.

