# SoundFields Plugin Overview

## 1. What this plugin does
- Adds support for basic audio soundfield (e.g., ambisonics) workflows.
- Provides encoding settings assets to configure soundfield rendering.
- Lightweight runtime-only feature set intended to be enabled by default.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Audio teams create/use `UAmbisonicsEncodingSettings` assets to configure soundfield encoding for ambisonics mixes.

## 3. Key Modules
- **SoundFields** (Runtime)
  - Role: Supplies soundfield encoding classes used by the audio engine.
  - Notable types: `UAmbisonicsEncodingSettings`.

## 4. Important Types & APIs
- `UAmbisonicsEncodingSettings` (extends `USoundfieldEncodingSettingsBase`)
  - Role: Asset describing ambisonics encoding parameters for use with soundfield submixes/renders.

## 5. Typical usage patterns
- Keep the plugin enabled (default) to allow selection of soundfield encoding settings in audio assets.
- Create or edit `UAmbisonicsEncodingSettings` assets and assign them to soundfield submixes or related audio objects that consume encoding settings.
- Combine with other spatial audio plugins (e.g., Spatialization) when building immersive mixes.

## 6. Version-specific notes (UE 5.7)
- Marked Beta in the `.uplugin`; no additional UE 5.7-specific notes found.

