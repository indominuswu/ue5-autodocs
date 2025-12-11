# Apple ProRes Decoder for Electra Plugin Overview

## 1. What this plugin does
- Adds Apple ProRes video decoding support to the Electra media pipeline.
- Provides a runtime module that registers the ProRes decoder for playback.

## 2. Key Modules
- **AppleProResDecoderElectra** (Runtime, PostEngineInit)
  - Role: Registers the ProRes decoder with Electra and exposes the module interface.

## 3. Important Types & APIs
- `FAppleProResDecoderElectraModule`
  - Role: Module implementation responsible for registering the decoder.
- `FElectraMediaProResDecoder`
  - Role: Decoder class used by Electra media player to handle ProRes streams.

## 4. Typical usage patterns
- Enable this plugin on platforms where ProRes playback via Electra is required.
- Use standard Media Framework playback; Electra will leverage the registered decoder automatically for ProRes content.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
