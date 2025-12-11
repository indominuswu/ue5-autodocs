# FLAC Audio Decoder for Electra Plugin Overview

## 1. What this plugin does
- Adds FLAC audio decoding support to the Electra media player stack.
- Registers an Electra codec that allows playback of FLAC streams on Win64 clients.
- Designed for media playback scenarios where Electra is used.

## 2. Key Modules
- **FlacDecoderElectra** (Runtime)
  - Role: Registers the FLAC decoder with Electra codecs during module startup.
  - Notable types: `FFlacDecoderElectraModule`, `FElectraMediaFlacDecoder`.

## 3. Important Types & APIs

### `FFlacDecoderElectraModule`
- Role: Module entry responsible for initializing/shutting down the FLAC decoder integration.

### `FElectraMediaFlacDecoder`
- Role: Codec implementation hooked into Electra’s codec registry to decode FLAC audio streams.

## 4. Typical usage patterns
- Enable the plugin on Win64 builds that rely on Electra playback; ensure the ElectraCodecs plugin is also enabled (declared dependency).
- Media opened through Electra will be able to decode FLAC audio without further setup.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific behaviors observed; plugin remains Win64-only and client-only (server denied).
