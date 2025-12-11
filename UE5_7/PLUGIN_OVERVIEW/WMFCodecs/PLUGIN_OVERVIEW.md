# WMFCodecs Plugin Overview

## 1. What this plugin does
- Adds Windows Media Foundation audio/video codecs to the AVCodecs stack on Win64.
- Provides WMF-based encoder implementations and configuration objects.
- Experimental and disabled by default; runtime-only with Win64 platform allow list.

## 2. Key Modules
- **WMFCodecs** (Runtime)
  - Role: Registers WMF audio/video encoders and their configurations (`AudioEncoderWMF`, `AudioEncoderConfigWMF`).
  - Depends on `AVCodecsCore`.

## 3. Important Types & APIs
### `AudioEncoderWMF` / `AudioEncoderConfigWMF`
- Role: WMF-backed audio encoder and configuration parameters for the AVCodecs pipeline.

## 4. Typical usage patterns
- Enable the plugin on Win64 builds alongside `AVCodecsCore`.
- Choose the WMF encoder through AVCodecs when encoding audio streams.
- Used at runtime for media capture or streaming workflows that need WMF hardware/software codecs.

## 5. Version-specific notes (UE 5.7)
- Marked experimental in the `.uplugin`; Win64-only support.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
