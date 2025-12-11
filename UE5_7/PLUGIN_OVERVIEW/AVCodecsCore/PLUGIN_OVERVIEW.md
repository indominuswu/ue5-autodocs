# AVCodecs Core Plugin Overview

## 1. What this plugin does

- Core audio/video codec infrastructure used by other Unreal features and plugins.
- Provides encoder/decoder abstractions, packet and buffer types, and codec configuration utilities for formats like AV1/H.264/H.265/VP8/VP9.
- Includes RHI-backed resource helpers to move video frames between CPU/GPU.
- No editor UI; intended for programmatic use in code that needs codec support.

## 2. Key Modules

- **AVCodecsCore** (Runtime)  
  - Role: Core codec framework (packet types, codec config, encoder/decoder interfaces, bitrate allocation, scalable video helpers).
- **AVCodecsCoreRHI** (Runtime)  
  - Role: Bridges codec resources to rendering hardware interfaces (D3D/Metal/Vulkan) and provides RHI-friendly video resource wrappers.

## 3. Important Types & APIs

- `FAVContext`, `FAVResource`, `FAVPacket`, `FAVResult`: Core structs for codec session context, resource description, packet payloads, and operation results.
- `FAudioEncoder` / `FAudioDecoder`, `FVideoEncoder` / `FVideoDecoder`: Base interfaces for implementing concrete codec backends.
- `FVideoBitrateAllocation`, `FVideoBitrateAllocator`, `FScalableVideoController` and related `ScalabilityStructure*` classes: Helpers for layered/scalable video encoding strategies.
- `FVideoResourceCPU`, `FVideoResourceD3D`, `FVideoResourceMetal`, `FVideoResourceVulkan`, `FVideoResourceRHI`: Wrappers for CPU and GPU frame storage.
- `FSimpleAudioEncoder` / `FSimpleVideoEncoder` / `FSimpleVideoDecoder`: Lightweight reference implementations built on the core interfaces.
- Codec-specific configs such as `FVideoDecoderConfigAV1/H264/H265/VP8/VP9` and encoder equivalents: Define format-specific capabilities and parameters.

## 4. Typical usage patterns

- Add `AVCodecsCore` (and `AVCodecsCoreRHI` when GPU resources are needed) as module dependencies in your plugin or game module.
- Use the codec interfaces to create encoders/decoders, feed `FAVPacket` data, and manage frame resources via CPU or RHI resource helpers.
- Combine bitrate allocator and scalable video controller helpers when building layered/temporal video encoding workflows.
- The plugin is infrastructure; other plugins (e.g., media capture/streaming) build on these classes rather than exposing end-user editor tools.

## 5. Version-specific notes (UE 5.7)

- Marked experimental in UE 5.7 and disabled by default.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
