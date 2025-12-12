# Resonance Audio Plugin Overview

## 1. What this plugin does
- Integrates Google’s Resonance Audio for spatialization and room acoustics.
- Provides ambisonics soundfield encoding/decoding, spatialization source settings, and reverb processing.
- Includes editor assets/factories and Blueprint helpers for runtime configuration.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Audio plugin users select Resonance for spatialization/soundfield/reverb and configure assets (`UResonanceAudioSpatializationSourceSettings`, `UResonanceAudioSettings`, Blueprint library).

## 3. Key Modules
- **ResonanceAudio** (Runtime)  
  - Spatialization, ambisonics encoding/decoding, reverb plugin, directivity visualization, and global settings.
- **ResonanceAudioEditor** (Editor)  
  - Asset factories and asset type actions for spatialization source settings.

## 4. Important Types & APIs
### `UResonanceAudioSpatializationSourceSettings` (configurable)
- Role: Spatialization plugin settings per source; controls directivity (`Pattern`, `Sharpness`), spread, distance attenuation curve, near/far distances.
- Functions: `DoesAudioComponentReferenceThis`, setters for max attenuation/near distance.

### `UResonanceAudioSoundfieldSettings`
- Role: Ambisonics encoding settings for Resonance Audio soundfield format; returns `ISoundfieldEncodingSettingsProxy`.

### `UResonanceAudioBlueprintFunctionLibrary`
- Role: Blueprint helpers for Resonance Audio (e.g., global control or visualization hooks).

### `UResonanceAudioSettings` (global config)
- Role: Global plugin settings pointing to default spatialization source settings asset.

### Reverb and spatialization processors
- `FResonanceAudioReverbPluginSettings` / `FResonanceAudioReverb`: room effect implementation with Blueprint-callable setters.
- `FResonanceAudioSpatialization` and ambisonics mixer/decoder classes implement the audio plugin interfaces.

## 5. Typical usage patterns
- Enable the plugin and select “Resonance Audio” as spatialization/reverb/soundfield in project audio settings.
- Create `ResonanceAudioSpatializationSourceSettings` assets; assign to audio components for per-source directivity/spread.
- Use the reverb effect on submixes or via audio volumes; adjust room parameters through Blueprint or settings.
- For ambisonics content, set soundfield settings to `ResonanceAudio` and use the provided encoding settings asset.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

