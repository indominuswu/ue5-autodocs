# Audio Synesthesia Plugin Overview

## 1. What this plugin does

- Provides offline audio analyzers and non-real-time (NRT) analysis assets for spectrum, loudness, onsets, LKFS, and Constant-Q transforms.
- Exposes analyzer settings assets and factories for authoring analysis configurations.
- Supports both runtime and editor workflows for extracting audio metadata and exposing it to Blueprints.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Content Browser assets/factories for analysis settings plus runtime analyzers usable from Blueprints.

## 3. Key Modules

- **AudioSynesthesiaCore** (Runtime)  
  - Role: Core analysis logic and data types.
- **AudioSynesthesia** (Runtime)  
  - Role: Analyzer settings assets and runtime execution.
- **AudioSynesthesiaEditor** (Editor)  
  - Role: Asset factories, editor integration, and asset type actions for analysis settings.

## 4. Important Types & APIs

### Analyzer settings (runtime)

- `UAudioSynesthesiaSettings`, `UAudioSynesthesiaNRTSettings`: Base classes for analyzer configuration.
- Specialized settings: `UConstantQSettings`, `UConstantQNRTSettings`, `ULoudnessSettings`, `ULoudnessNRTSettings`, `UMeterSettings`, `ULKFSSettings`, `ULKFSNRTSettings`, `UOnsetNRTSettings`, `USynesthesiaSpectrumAnalysisSettings`.
- Roles: Configure FFT/windowing, frequency ranges, loudness targets, meter ballistics, and onset detection parameters for offline analysis.

### Editor factories and asset actions

- Factories such as `UAudioSynesthesiaSettingsFactory` and `UAudioSynesthesiaNRTSettingsFactory` create analysis asset instances.
- Asset type actions expose analyzers in the Content Browser and Sequencer.

## 5. Typical usage patterns

- Enable the plugin; create analyzer settings assets (e.g., Constant Q, Loudness, Meter) in the Content Browser.
- Use the analyzers in offline/NRT workflows to extract metadata from sound assets and drive gameplay or visualization.
- Reference the analyzer assets in Blueprints or code to request analyzed data (e.g., loudness curves, onset events).
- Use editor asset type actions to duplicate/tweak analyzer presets for different content.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

