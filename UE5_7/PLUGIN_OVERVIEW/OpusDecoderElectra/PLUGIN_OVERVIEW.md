# OpusDecoderElectra Plugin Overview

## 1. What this plugin does

- Provides Opus audio decoding for the Electra media player pipeline.
- Adds a runtime module that registers an Opus decoder with Electra for media playback.

## 2. Editor/Runtime surfaces

- User-facing: No - Internal Electra codec hook; automatically registers an Opus decoder with no editor/runtime APIs exposed to users.

## 3. Key Modules

- **OpusDecoderElectra** (Runtime)  
  - Role: Hooks into Electra’s decoder factory to supply Opus decoding capabilities.

## 4. Important Types & APIs

- `FElectraOpusDecoder` (`ElectraMediaOpusDecoder.h`)  
  - Decoder implementation bridging Opus bitstreams to Electra audio output.
- `FOpusDecoderElectraModule` (`OpusDecoderElectraModule.h`)  
  - Module bootstrap that registers the decoder on startup.

## 5. Typical usage patterns

- Enable when using Electra to play media streams containing Opus audio (e.g., web streams).
- No editor UI; usage is automatic when Electra encounters Opus tracks and the plugin is enabled.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current Electra Opus decoder integration in the UE 5.7 source tree.

