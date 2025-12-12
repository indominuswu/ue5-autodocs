# NFORDenoise Plugin Overview

## 1. What this plugin does

- Implements a spatial-temporal denoiser for the Unreal Path Tracer (with MRQ focus) based on Nonlinearly Weighted First-order Regression (NFOR).
- Intended to denoise Monte Carlo renderings by blending neighboring samples across space and time.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Registers the `FNFORDenoiser` via `RegisterSpatialTemporalDenoiser` so users can pick the NFOR denoiser in Path Tracer/Movie Render Queue renders; tuning happens through render settings/cvars (e.g., `r.NFOR.Feature.Depth`).

## 3. Key Modules

- **NFORDenoise** (RuntimeAndProgram) – Denoiser module and log category.

## 4. Important Types & APIs

### `FNFORDenoiseModule`

- `IModuleInterface` implementation that wires up the denoiser and exposes the `LogNFORDenoise` category.

## 5. Typical usage patterns

- Enable the plugin when rendering with Path Tracer/Movie Render Queue to apply the NFOR-based denoiser; configuration is handled through rendering integration points rather than explicit user-facing assets.

## 6. Version-specific notes (UE 5.7)

- No UE 5.7-specific notes surfaced in the module code.

