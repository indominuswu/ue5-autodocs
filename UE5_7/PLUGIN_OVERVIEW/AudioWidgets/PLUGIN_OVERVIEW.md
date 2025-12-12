# AudioWidgets Plugin Overview

## 1. What this plugin does

- Provides reusable UMG widgets for audio metering, spectrograms, and analyzer visualizations.
- Bridges audio analysis data (e.g., Synesthesia analyzers) into UI components.
- Supplies supporting rack-unit settings structures for configuring widget displays.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Exposes UMG widgets and editor support for audio meters/spectrogram visualizations.

## 3. Key Modules

- **AudioWidgetsCore** (RuntimeAndProgram)  
  - Role: Core widget logic and shared data types.
- **AudioWidgets** (Runtime)  
  - Role: Concrete UMG widgets and runtime presentation code.
- **AudioWidgetsEditor** (Editor)  
  - Role: Editor integrations for widget assets and design-time support.

## 4. Important Types & APIs

- Widget classes reference analyzer settings such as `UMeterSettings`, `USynesthesiaSpectrumAnalysisSettings`, `UConstantQSettings`, `ULKFSSettings` to drive visuals.
- Rack-unit settings structs (`FSpectrogramRackUnitSettings`, `FSpectrumAnalyzerRackUnitSettings`, `FLoudnessMeterRackUnitSettings`) configure visual behavior (resolution, ranges, colors).

## 5. Typical usage patterns

- Enable the plugin; add Audio Widgets (meter, spectrogram, spectrum analyzer) to UMG layouts.
- Feed widgets with analysis data produced by Audio Synesthesia analyzers or runtime audio meters.
- Adjust rack-unit settings in Blueprints or defaults to match desired meter/spectrogram ranges and styling.
- Use alongside `AudioInsights` for consistent visualization across debug tools and in-game HUDs.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
