# NNEDenoiser Plugin Overview

## 1. What this plugin does

- Provides a neural-network-based denoiser for the Unreal Path Tracer using the Neural Network Engine (NNE).
- Supplies assets to describe model data, IO mappings, and tiling for temporal/static denoisers.
- Includes shader support for runtime execution.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Users create `UNNEDenoiserAsset` data assets (with mapping data tables and tiling configs) to drive NNE denoisers in Path Tracer/Movie Render Queue workflows.

## 3. Key Modules

- **NNEDenoiser** (Runtime) – Denoiser assets, IO mapping types, runtime integration.
- **NNEDenoiserShaders** (Runtime) – Shader code required to run the denoiser models.

## 4. Important Types & APIs

### `UNNEDenoiserAsset`

- `UDataAsset` holding references to NNE model data (`UNNEModelData`), input/output mapping tables, and `FTilingConfig`.
- Blueprint-editable for selecting model files and mapping data tables.

### IO mapping data (`FNNEDenoiserInputMappingData`, `FNNEDenoiserOutputMappingData`, `FNNEDenoiserTemporalInputMappingData`, `FNNEDenoiserTemporalOutputMappingData`)

- Table row structs mapping tensors/channels to logical resources (`Color`, `Albedo`, `Normal`, `Flow`, `Output`) for static/temporal denoisers.
- Enums (`EInputResourceName`, `EOutputResourceName`, `ETemporalInputResourceName`, `ETemporalOutputResourceName`) describe available resources.

### `FNNEDenoiserResourceName` / `FTilingConfig`

- Utility and configuration types controlling resource naming and tile sizing when executing denoiser models.

## 5. Typical usage patterns

- Create an `NNEDenoiserAsset` referencing an NNE model and mapping data tables; adjust tiling for GPU memory constraints.
- Use the asset in path-tracing or Movie Render Queue setups that support NNE denoisers; mappings define how render targets feed the network and where outputs are written.
- Customize input/output mapping tables to align with the channels expected by the chosen model.

## 6. Version-specific notes (UE 5.7)

- No UE 5.7-specific notes surfaced; overview reflects current assets and enums.

