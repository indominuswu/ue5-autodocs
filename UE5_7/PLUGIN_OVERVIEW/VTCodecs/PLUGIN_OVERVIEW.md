# VTCodecs Plugin Overview

## 1. What this plugin does
- Adds Apple Video Toolbox-based codecs to the AVCodecs stack on macOS.
- Provides Video Toolbox decoders/encoders and associated configuration objects.
- Experimental and disabled by default; runtime-only with Mac platform allow list.

## 2. Key Modules
- **VTCodecs** (Runtime)
  - Role: Registers Video Toolbox video encoder/decoder implementations (`VideoDecoderVT`, `VideoEncoderVT`) and configs.
- **VTCodecsRHI** (Runtime)
  - Role: RHI-level support required for the codecs (Mac-only).

## 3. Important Types & APIs
### `VideoDecoderVT` / `VideoDecoderConfigVT`
- Role: Implements Video Toolbox-backed video decoding and configuration parameters.

### `VideoEncoderVT` / `VideoEncoderConfigVT`
- Role: Implements Video Toolbox-backed video encoding and configuration parameters.

### `NaluRewriter`, `VTSessionHelpers`
- Role: Helpers for packetizing and configuring Video Toolbox sessions (e.g., NALU handling).

## 4. Typical usage patterns
- Enable the plugin on Mac builds alongside `AVCodecsCore`.
- Select or register Video Toolbox codecs through the AVCodecs pipeline; configure via the provided config objects.
- Used at runtime for media playback or capture workflows that require VT hardware codecs.

## 5. Version-specific notes (UE 5.7)
- Marked experimental in the `.uplugin`; Mac-only support.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
