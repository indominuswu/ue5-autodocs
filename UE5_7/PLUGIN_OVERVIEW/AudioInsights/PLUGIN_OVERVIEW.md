# Audio Insights Plugin Overview

## 1. What this plugin does

- Suite of tools to profile, debug, and monitor audio performance and content within the editor.
- Provides dashboards for spectrograms, spectrum analyzers, loudness meters, and sound hierarchies.
- Includes editor settings to configure visible columns, viewing modes, and meter defaults.

## 2. Key Modules

- **AudioInsights** (EditorAndProgram)  
  - Role: Core UI and data providers for audio profiling views.
- **AudioInsightsEditor** (Editor)  
  - Role: Editor integration, settings panels, and layout configuration.

## 3. Important Types & APIs

### `UAudioInsightsEditorSettings` (UDeveloperSettings)

- Role: Editor-per-project settings for Audio Insights tools.
- Key properties: `SpectrogramSettings`, `SpectrumAnalyzerSettings`, `LoudnessMeterSettings`, viewing and auto-expand preferences.

### UI helpers

- Various view factories (e.g., `SoundDashboardViewFactory`) and menu settings classes manage visible columns and tree viewing modes.

## 4. Typical usage patterns

- Enable the plugin (enabled by default); open Audio Insights from the Window/Audio menu to inspect audio performance.
- Configure display preferences via Editor Settings → Audio Insights to adjust spectrogram/analyzer defaults and visible data columns.
- Use dashboards to monitor loudness, spectrum, and other metrics while playing in editor or connecting to running sessions.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
