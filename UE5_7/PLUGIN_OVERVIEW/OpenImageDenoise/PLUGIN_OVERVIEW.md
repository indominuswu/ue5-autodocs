# OpenImageDenoise Plugin Overview

## 1. What this plugin does

- Integrates Intel Open Image Denoise (OIDN) as a denoiser for the Path Tracer.
- Adds console-configurable denoise passes for color/alpha and optional auxiliary buffers (albedo/normal).
- Provides a runtime module that registers the OIDN denoiser when available on the target platform.

## 2. Key Modules

- **OpenImageDenoise** (ClientOnly)  
  - Role: Runtime denoiser module; registers with the renderer and exposes console variables for OIDN behavior.

## 3. Important Types & APIs

- `FOpenImageDenoiseModule` (`Plugin.cpp`)  
  - Module that registers/unregisters the denoiser; wraps OIDN device/context creation.
- Console variables  
  - `r.OIDN.DenoiseAlpha` – include alpha in the denoise pass.  
  - `r.OIDN.DenoiseAuxilaryInputs` – pre-denoise auxiliary buffers.  
  - `r.OIDN.UseAuxilaryInputs` – use albedo/normal buffers for higher quality.
- Internal structs `FDenoiseSettings`, `FDenoiseTextureParameters`  
  - Capture current console configuration and RDG texture bindings for the denoiser.

## 4. Typical usage patterns

- Enable the plugin for path-traced renders; OIDN activates when `WITH_INTELOIDN` is true for the platform.
- Adjust quality/performance via the `r.OIDN.*` console variables; auxiliary buffers improve quality at extra cost.
- No editor UI is provided; configuration is via console/ini settings or custom render pipeline integration.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview reflects the current OIDN integration in the UE 5.7 source tree.
