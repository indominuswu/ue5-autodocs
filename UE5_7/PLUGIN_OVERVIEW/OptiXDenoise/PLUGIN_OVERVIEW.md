# OptiXDenoise Plugin Overview

## 1. What this plugin does

- Integrates NVIDIA OptiX AI denoiser for the Path Tracer.
- Provides GPU-accelerated denoise passes for rendered frames, using OptiX libraries when available.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Registers the OptiX Path Tracer denoiser used in render settings/Movie Render Queue, controlled through renderer options/console variables when OptiX is present.

## 3. Key Modules

- **OptiXDenoise** (RuntimeAndProgram)  
  - Role: Registers the OptiX denoiser and links against the OptiX SDK; includes program binaries when needed.

## 4. Important Types & APIs

- `FOptiXDenoiser` (`OptiXDenoiser.h`)  
  - Implements denoising flow, command list integration, and buffer management.
- Third-party helpers (`OptiXDenoiseBase.h`, `OptiXDenoiserFunctionList.h`, `OptiXCudaFunctionList.h`)  
  - Wrap the OptiX and CUDA entry points used by the module.

## 5. Typical usage patterns

- Enable for path-traced renders on NVIDIA GPUs with OptiX available; the denoiser activates at render time with no editor UI.
- Configure behavior via renderer settings/console variables that select denoiser modes (standard Path Tracer controls).
- Ensure OptiX runtime dependencies are present for target builds; otherwise the denoiser will be unavailable.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview reflects the OptiX denoiser integration in the UE 5.7 source tree.

