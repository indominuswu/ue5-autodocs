# Warp Utils Plugin Overview

## 1. What this plugin does

- Provides Blueprint-accessible utilities for generating and exporting PFM warp maps (e.g., for MPCDI/nDisplay workflows).
- Includes helper functions to procedurally generate PFM data from scene parameters or to write supplied vertex data.
- Runtime plugin (Win64 allow list for PFM export) marked beta.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Blueprint libraries (`UWarpUtilsBlueprintLibrary`, `UPFMExporterBlueprintLib`) that users call to generate/save PFM warp maps for projection setups.

## 3. Key Modules

- **PFMExporter** (Runtime) – Implements PFM file writing/generation helpers; platform-allowed on Win64.
- **WarpUtils** (Runtime) – Shared Blueprint utility library for warp-related operations.

## 4. Important Types & APIs

### `UWarpUtilsBlueprintLibrary`

- Role: Blueprint function library for PFM operations.
- Key functions:
  - `SavePFM` / `SavePFMEx`: Write PFM files from an array of `FVector` vertices (with optional validity flags).
  - `GeneratePFM` / `GeneratePFMEx`: Procedurally generate PFM data from starting transform, tiling, angles, pixel sizes, and validity flags, then save to file.

### `UPFMExporterBlueprintLib` (PFMExporter module)

- Role: Additional Blueprint API wrapper for PFM export (mirrors the functions above for the exporter module).

## 5. Typical usage patterns

- Enable the plugin on Win64. From Blueprint (or C++), call `GeneratePFM`/`SavePFM` to author warp PFM files for projection systems.
- Provide tile counts, angles, and pixel dimensions to `GeneratePFM` to synthesize a PFM layout; or pass raw vertex data to `SavePFM` if you already computed the warp geometry.
- Use extended variants when you need to mark invalid tiles (NaN handling) to indicate holes in the warp map.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

