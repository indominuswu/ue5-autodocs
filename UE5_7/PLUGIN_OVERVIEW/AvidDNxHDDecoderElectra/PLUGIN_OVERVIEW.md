# Avid DNxHDR decoder for Electra Plugin Overview

## 1. What this plugin does

- Adds an Electra media pipeline decoder for Avid DNxHD/R codecs.
- Targets playback scenarios where Electra needs to decode DNx media streams.
- Runtime-only; no editor UI or content.

## 2. Editor/Runtime surfaces
- User-facing: No - Backend Electra decoder registration for DNxHD/DNxHR; no direct editor or Blueprint surfaces.

## 3. Key Modules

- **AvidDNxHDDecoderElectra** (Runtime)  
  - Role: Registers a DNx decoder implementation with Electra.

## 4. Important Types & APIs

- `FAvidDNxHDDecoderElectraModule`: Module entry registering the decoder with Electra.
- `FElectraMediaAvidDNxHDDecoder`: Decoder class used by Electra to handle DNxHD/DNxHR bitstreams.

## 5. Typical usage patterns

- Enable the plugin when Electra playback of DNxHD/DNxHR sources is required.
- Media playback automatically selects the decoder when encountering DNx streams; no Blueprint or editor interaction is needed.

## 6. Version-specific notes (UE 5.7)

- Disabled by default; intended for projects needing DNx decoding.
- No explicit UE 5.7-specific notes found; overview reflects the current implementation.

