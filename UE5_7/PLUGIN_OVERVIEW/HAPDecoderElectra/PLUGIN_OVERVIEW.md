# HAP Decoder for Electra Plugin Overview

## 1. What this plugin does
- Adds HAP video codec decoding to the Electra media pipeline.
- Targets high-resolution GPU-friendly playback of HAP-encoded media streams.
- Operates transparently through Electra-based media players; no user-facing UI.

## 2. Editor/Runtime surfaces

- User-facing: No - Backend Electra decoder; end users just enable it so HAP media plays, with no editor or Blueprint surface.

## 3. Key Modules
- **HAPDecoderElectra** (Runtime)  
  - Role: Registers HAP decoder implementations (e.g., `ElectraMediaHAPDecoder`) with the Electra backend so media players can open HAP assets.

## 4. Important Types & APIs
- Module-level classes are internal; no public UObject APIs are exposed. Decoder registration is handled inside the module (`HAPDecoderElectraModule`, `ElectraMediaHAPDecoder`).

## 5. Typical usage patterns
- Enable the plugin on platforms where Electra is used; open HAP-encoded media through standard `MediaPlayer`/Electra players and the decoder will be chosen automatically.
- No Blueprint or editor setup is required beyond enabling the plugin and packaging the decoder with the target platform.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

