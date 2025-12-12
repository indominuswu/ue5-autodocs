# Waveform Editor Plugin Overview

## 1. What this plugin does
- Adds editor tooling for viewing and editing waveform assets with transformations and visualization widgets.
- Provides transformation settings (e.g., time/pitch edits) and export helpers for audio data.
- Supplies reusable waveform widgets for editor UI and details customizations.
- Beta and disabled by default.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor-only waveform editor panels, widgets, and transformation tools for audio assets.

## 3. Key Modules
- **WaveformEditor** (Editor)
  - Role: Core editor integration, instantiation, details customizations, and transformation settings (`WaveformEditorTransformationsSettings`, `WaveformEditorInstantiator`).
- **WaveformEditorWidgets** (Editor)
  - Role: Slate widgets and visualization components for waveform display and interaction.
- **WaveformTransformations** (Editor, PreDefault)
  - Role: Implements waveform transformation logic and helpers (`TransformedWaveformView`, `WaveformEditorWaveWriter`).
- **WaveformTransformationsWidgets** (Editor)
  - Role: UI widgets for configuring and previewing transformations.

## 4. Important Types & APIs
### `IWaveformEditorModule` / `IWaveformEditorInstantiator`
- Role: Entry points to create waveform editor instances and integrate with asset toolkits.

### `WaveformEditorTransformationsSettings`
- Role: Settings object controlling which transformations are available and their parameters.

### `TransformedWaveformView` and `TransformedWaveformViewFactory`
- Role: Provides a transformed view of waveform data for visualization and export.

### `WaveformEditorDetailsCustomization` / `IWaveformEditorDetailsProvider`
- Role: Customizes details panel exposure of waveform properties and transformation controls.

## 5. Typical usage patterns
- Enable the plugin (and dependencies like AudioSynesthesia and AudioWidgets).
- Open an audio asset with the Waveform Editor; use transformation settings to apply edits.
- Use provided widgets to visualize, scrub, and export transformed waveforms.
- Extend transformations via the `WaveformTransformations` module if needed.

## 6. Version-specific notes (UE 5.7)
- Marked beta in the `.uplugin`.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
