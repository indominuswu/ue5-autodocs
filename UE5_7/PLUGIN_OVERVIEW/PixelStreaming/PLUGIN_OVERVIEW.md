# Pixel Streaming Plugin Overview

## 1. What this plugin does
- Streams UE rendering/audio to WebRTC-capable clients (e.g., browsers), with input round-trip back to the engine.
- Provides runtime capture, encoding, signalling, and player/session management plus Blueprint helpers and editor tools.
- Supports HMD integration and multiple backends/codecs (NV, AMF, VT) through dependent codec plugins.

## 2. Key Modules
- **PixelStreaming** (Runtime)  
  - Role: Core WebRTC integration, streamer/session management, capture/input routing, settings, stats, signalling.
- **PixelStreamingServers** (Runtime)  
  - Role: Helper logic for the bundled signalling/turn servers.
- **PixelStreamingEditor** (UncookedOnly)  
  - Role: Editor hooks and tooling for configuring/launching streaming in PIE/Editor.
- **PixelStreamingBlueprint** (Runtime)  
  - Role: Blueprint exposure of streaming API (streamers, input, events).
- **PixelStreamingBlueprintEditor** (Editor)  
  - Role: Editor support for the Blueprint module.
- **PixelStreamingHMD** (Runtime)  
  - Role: HMD-specific input/pose handling for streamed sessions.
- **PixelStreamingInput** (Runtime)  
  - Role: Input device routing from WebRTC data channels back into the engine.

## 3. Important Types & APIs
- Core interfaces: `IPixelStreamingModule`, `IPixelStreamingStreamer`, `IPixelStreamingSignallingConnection`, `IPixelStreamingStats`, `IPixelStreamingAudioSink/Input/Consumer`, `IPixelStreamingVideoInput` (and RHI/RenderTarget/NV12/I420/PIEViewport/backbuffer variants).  
  - Role: Drive capture sources, signalling, and media pipeline.
- Components:  
  - `UPixelStreamingInputComponent`: receives WebRTC input events (keyboard/mouse/touch/gamepad) and forwards to the engine.  
  - `UPixelStreamingAudioComponent`: routes audio to streaming peers.  
  - `UPixelStreamingVideoInput*` classes: wrap different video sources.  
- Networking/signalling: `FPixelStreamingPeerConnection`, `FPixelStreamingDataChannel`, `FPixelStreamingSignallingConnection`.  
- Configuration: `UPixelStreamingSettings` and `FPixelStreamingPlayerConfig` for stream/session options; `PixelStreamingCodec` helpers select encoder codecs.  
- Utilities: `PixelStreamingBufferBuilder`, `PixelStreamingUtils`, `PixelStreamingTrace`/`StatNames` for diagnostics.

## 4. Typical usage patterns
- Enable Pixel Streaming plus dependencies (`PixelCapture`, codecs, WebSocketNetworking, MediaIOFramework).  
- Configure settings (`PixelStreaming` project settings) for signalling servers, codecs, resolutions, input handling.  
- In Blueprint or C++, create/get a streamer (`IPixelStreamingModule`), register input/audio/video sources, and start streaming.  
  - Add `UPixelStreamingInputComponent` to actors needing WebRTC input.  
  - Use `PixelStreamingBlueprint` nodes for start/stop streaming, send custom data channel messages, and respond to viewer connections.  
- Launch signalling/turn servers (via provided scripts or custom deployment) and connect WebRTC clients to receive the stream.

## 5. Version-specific notes (UE 5.7)
- Plugin is stable (not marked beta) but depends on platform codec plugins and `PixelCapture`.  
- No explicit UE 5.7-only changes noted; overview reflects the 5.7 source tree.
