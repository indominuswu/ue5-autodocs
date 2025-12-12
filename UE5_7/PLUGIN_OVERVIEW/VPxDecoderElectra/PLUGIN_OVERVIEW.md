# VPxDecoderElectra Plugin Overview

## 1. What this plugin does

- Adds VPx (e.g., VP8/VP9) codec support to the Electra media playback pipeline.
- Provides decoder registration so Electra streams encoded with VPx can be played back by Unreal’s media framework.
- Runtime-only module with no public UObject APIs.

## 2. Editor/Runtime surfaces

- User-facing: No - Codec backend for Electra media playback; no direct editor/runtime interfaces beyond enabling the decoder.

## 3. Key Modules

- **VPxDecoderElectra** (Runtime)  
  - Role: Registers the VPx decoder with Electra’s codec factory.  
  - Notable files: `VPxDecoderElectraModule`, `ElectraMediaVPxDecoder`.

## 4. Important Types & APIs

- The module exposes codec registration internally; there are no Blueprint or UObject-facing types. Media playback routes through Electra once the plugin is enabled.

## 5. Typical usage patterns

- Enable the plugin when your project needs to play VPx-encoded streams via Electra Media Player.
- Use standard MediaPlayer/MediaSource assets; Electra will pick the VPx decoder when encountering VP8/VP9 content.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

