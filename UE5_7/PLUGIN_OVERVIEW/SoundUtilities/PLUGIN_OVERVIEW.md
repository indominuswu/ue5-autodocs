# Sound Utilities Plugin Overview

## 1. What this plugin does
- Supplies a Blueprint function library with common audio math/helpers (tempo, MIDI, decibel conversions).
- Provides lightweight utilities for audio scripting without requiring additional assets.
- Includes editor module stub for integration with audio tooling.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Exposes Blueprint callable audio utility functions for designers/scripters; minimal editor integration.

## 3. Key Modules
- **SoundUtilities** (Runtime)
  - Role: Hosts the Blueprint library of audio utility functions.
  - Notable types: `USoundUtilitiesBPFunctionLibrary`.
- **SoundUtilitiesEditor** (Editor)
  - Role: Editor integration (no major public types; supports the runtime library in editor workflows).

## 4. Important Types & APIs
- `USoundUtilitiesBPFunctionLibrary` (UBlueprintFunctionLibrary)
  - Role: Exposes static BlueprintCallable helpers for audio math.
  - Key functions: `GetBeatTempo`, `GetFrequencyFromMIDIPitch`, `GetMIDIPitchFromFrequency`, `GetPitchScaleFromMIDIPitch`, `GetGainFromMidiVelocity`, `ConvertLinearToDecibels`, `ConvertDecibelsToLinear`, `GetLogFrequencyClamped`, `GetLinearFrequencyClamped`, `GetFrequencyMultiplierFromSemitones`, `GetBandwidthFromQ`, `GetQFromBandwidth`.

## 5. Typical usage patterns
- Enable the plugin (Beta) and call the Blueprint nodes in audio graphs or gameplay scripts for tempo/MIDI/log-frequency conversions.
- Use conversion helpers when mapping UI sliders to frequency ranges or computing gain from MIDI velocity.
- No dedicated assets required; functions are pure/static and safe for runtime or editor utility use.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
