# Synthesis and DSP Effects Plugin Overview

## 1. What this plugin does
- Provides a suite of realtime synthesizers (modular synth, granular, wavetable, sample player, tone generator) and DSP source/submix effects.
- Ships with Blueprint libraries and preset assets for modular synths and wave tables.
- Editor module supplies asset editing tools and UI for configuring synthesizer presets.

## 2. Key Modules
- **Synthesis** (Runtime, PreDefault) – Synth component implementations, DSP effects, presets, and Blueprint utilities.
- **SynthesisEditor** (Editor) – Editor support for synth-related assets and UI customization.

## 3. Important Types & APIs
- Components: `UModularSynthComponent`, `UGranularSynth`, `USynthComponentMonoWaveTable`, `USynthSamplePlayer`, `USynthComponentToneGenerator`, `UEnvelopeFollowerListener`.
- Presets/Assets: `UModularSynthPresetBank`, `UModularSynthLibrary` (Blueprint lib to add presets), `UMonoWaveTableSynthPreset`.
- Effects: Source/Submix effect settings (e.g., convolution reverb, multiband compressor, envelope follower) with update methods to push new settings at runtime.
- Utilities: `USynthesisUtilitiesBlueprintFunctionLibrary` for helper math/audio functions.

## 4. Typical usage patterns
- Add synth components to actors/Blueprints and route their output to submixes; configure presets via preset assets or Blueprint setters.
- Use `UModularSynthLibrary::AddModularSynthPresetToBankAsset` to manage preset banks.
- Apply DSP source/submix effects (convolution reverb, multiband compressor, etc.) by creating effect presets and assigning them to audio components or submixes.
- Use the editor tools to author modular synth or wavetable presets visually.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; plugin is enabled by default and stable.

