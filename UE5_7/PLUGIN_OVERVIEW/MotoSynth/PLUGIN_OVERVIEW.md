# MotoSynth Plugin Overview

## 1. What this plugin does

- Experimental granular synthesis engine for vehicle/engine audio.
- Provides runtime and editor support for MotoSynth presets and sources.
- Supplies a synth component that renders engine audio driven by runtime parameters.
- Disabled by default; intended for experimentation.

## 2. Editor/Runtime surfaces

- User-facing: Yes - `USynthComponentMoto` lets users attach granular engine synthesis to actors and drive it with runtime settings.
- User-facing: Yes - Editor module ships factories/editors for `UMotoSynthSource` and `UMotoSynthPreset` assets so users can author engine audio.

## 3. Key Modules

- **MotoSynth** (Runtime) — MotoSynth engine, source assets, presets, and synth component.
- **MotoSynthEditor** (Editor) — editor UI and asset factories for creating/editing MotoSynth sources and presets.

## 4. Important Types & APIs

- `USynthComponentMoto` — synth component that plays MotoSynth audio; accepts runtime settings.
- `UMotoSynthPreset` — asset storing `FMotoSynthRuntimeSettings` for the synth component.
- `UMotoSynthSource` (via `UMotoSynthSourceAsset`) — source asset containing granular engine source data.
- `FMotoSynthRuntimeSettings` — runtime parameters controlling pitch curves, envelopes, and synthesis behavior.

## 5. Typical usage patterns

- Enable the plugin, create MotoSynth Source and Preset assets in the editor, then place a `USynthComponentMoto` on an actor.
- Assign a preset to the component and drive RPM/acceleration parameters at runtime to render engine sounds.
- Use the editor module to author or tweak source/preset assets; swap presets for different vehicle profiles.

## 6. Version-specific notes (UE 5.7)

- Plugin remains experimental in 5.7; no additional version-specific flags noted.

