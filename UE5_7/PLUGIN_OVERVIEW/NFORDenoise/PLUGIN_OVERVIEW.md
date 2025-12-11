# NFORDenoise Plugin Overview

## 1. What this plugin does

- Implements a spatial-temporal denoiser for the Unreal Path Tracer (with MRQ focus) based on Nonlinearly Weighted First-order Regression (NFOR).
- Intended to denoise Monte Carlo renderings by blending neighboring samples across space and time.

## 2. Key Modules

- **NFORDenoise** (RuntimeAndProgram) – Denoiser module and log category.

## 3. Important Types & APIs

### `FNFORDenoiseModule`

- `IModuleInterface` implementation that wires up the denoiser and exposes the `LogNFORDenoise` category.

## 4. Typical usage patterns

- Enable the plugin when rendering with Path Tracer/Movie Render Queue to apply the NFOR-based denoiser; configuration is handled through rendering integration points rather than explicit user-facing assets.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific notes surfaced in the module code.

