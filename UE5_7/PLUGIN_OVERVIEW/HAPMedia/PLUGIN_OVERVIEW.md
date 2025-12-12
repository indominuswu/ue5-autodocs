# HAP Media Plugin Overview

## 1. What this plugin does
- Adds HAP codec playback support to the media framework (WMF-based path).
- Targets GPU-friendly decoding of HAP video for high-resolution playback.
- Operates behind existing media player interfaces; no standalone editor UI.

## 2. Editor/Runtime surfaces

- User-facing: No - Backend HAP decoder for WMF media playback; no direct editor or Blueprint surface beyond enabling the plugin.

## 3. Key Modules
- **HAPMedia** (Runtime)  
  - Role: Registers a HAP decoder (`WmfMediaHAPDecoder`) and supporting module glue so WMF media playback can decode HAP streams.

## 4. Important Types & APIs
- Decoder implementation is internal to the module; no public UObject types are exported. The module hooks into the media player factory chain.

## 5. Typical usage patterns
- Enable the plugin on platforms using the WMF media player; open HAP-encoded media through `MediaPlayer` and the decoder will be used automatically when available.
- No additional Blueprint nodes are required; use standard media textures/players.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

