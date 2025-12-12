# Wave Tables Plugin Overview

## 1. What this plugin does

- Adds a default WaveTable implementation to the Unreal audio engine for building oscillators and sampled tables.
- Supports importing audio/curve data into WaveTable banks and sampling them at runtime.
- Includes editor tooling for editing WaveTable curves, banks, and transforms.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime WaveTable assets/samplers plus editor UI for bank/curve editing and import.

## 3. Key Modules

- **WaveTable** (Runtime)
  - Role: Core WaveTable data structures (`FWaveTableSettings`, `FWaveTableBank`, sampler/transforms) and import utilities.
- **WaveTableEditor** (Editor)
  - Role: Editor UI for editing banks/curves, bank asset helpers, and waveform/transform layout utilities.

## 4. Important Types & APIs

### `FWaveTableSettings`
- Role: Import/edit settings for a WaveTable entry (file path, channel index, phase/trim/fade, normalization, offset removal, resolution/sampling mode).
- Key enums: `EWaveTableResolution`, `EWaveTableSamplingMode`, and `EWaveTableCurve` (linear/exp/log/sin/custom/file-based shapes).

### `UWaveTableBank`
- Role: Data asset holding a collection of WaveTable entries and metadata for playback/sampling.

### `FWaveTableSampler` / `FWaveTableTransform`
- Role: Runtime sampling helpers and per-entry transform data used to shape tables into oscillators or envelopes.

### `WaveTable::RatioToIndex`
- Role: Utility converting 0?1 ratios to sample indices for tables.

### Editor types
- `UWaveTableBankEditor`, `FWaveTableCurveEditorViewStacked`, and layout/transform helpers provide curve editing and import UX inside the WaveTable Editor module.

## 5. Typical usage patterns

- Enable the plugin, create a `WaveTableBank` asset, and import audio/curves via the bank editor UI.
- Configure per-entry `FWaveTableSettings` (resolution vs. fixed sample rate, fades, normalization, phase) and author curves (`EWaveTableCurve::Custom` or shared curve assets).
- At runtime, use WaveTable sampler utilities and transforms to generate audio from bank entries; integrate with synths or custom audio components.

## 6. Version-specific notes (UE 5.7)

- Marked beta. No explicit UE 5.7-specific behaviors were identified beyond current API state.
