# AMFCodecs Plugin Overview

## 1. What this plugin does
- Adds AMD Advanced Media Framework (AMF) video codecs to the AVCodecs system.
- Provides runtime encoder/decoder implementations that leverage AMF on supported GPUs.

## 2. Key Modules
- **AMFCodecs** (Runtime)
  - Role: Codec integration, encoder/decoder creation using AMF APIs.
- **AMFCodecsRHI** (Runtime)
  - Role: RHI-side helpers/config to interface codecs with rendering.

## 3. Important Types & APIs

### `FVideoEncoderAMF` / `FVideoDecoderAMF`
- Role: Implement video encode/decode using AMF; configured via `FVideoEncoderConfigAMF` and `FVideoDecoderConfigAMF`.

### `FAMFModule`
- Role: Module bootstrap for registering AMF codecs with AVCodecs.

## 4. Typical usage patterns
- Enable AMFCodecs along with AVCodecs; select AMF-based encoders/decoders in capture or streaming configurations that support hardware-accelerated codecs on AMD GPUs.
- Configure encoder/decoder settings through the AVCodecs interfaces using the AMF-specific config structs.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.