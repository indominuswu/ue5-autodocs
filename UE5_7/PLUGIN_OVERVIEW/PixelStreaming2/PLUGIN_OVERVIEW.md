# Pixel Streaming 2 Plugin Overview

## 1. What this plugin does
- Next-generation Pixel Streaming stack for streaming UE video/audio over WebRTC.
- Breaks the pipeline into modular producer/consumer interfaces for video and audio.
- Ships editor tooling, settings, RTC integration, input handling, HMD support, and bundled server helpers.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Developer-facing WebRTC streaming stack with configurable settings and producer/consumer interfaces (`IPixelStreaming2VideoProducer`, `IPixelStreaming2AudioProducer`, `IPixelStreaming2Streamer`, input/HMD modules) for building streamed experiences.

## 3. Key Modules
- **PixelStreaming2Core** (Runtime)  
  - Role: Core media interfaces for producers/consumers/sinks (video/audio) and streamer abstraction.
- **PixelStreaming2** (Runtime)  
  - Role: Primary implementation layer building on the core interfaces.
- **PixelStreaming2Settings** (Runtime)  
  - Role: Settings/configuration for Pixel Streaming 2.
- **PixelStreaming2RTC** (Runtime)  
  - Role: WebRTC integration for signalling and transport.
- **PixelStreaming2Servers** (Runtime)  
  - Role: Helper logic for bundled signalling/turn servers.
- **PixelStreaming2Editor** (Editor)  
  - Role: Editor-facing hooks and tooling.
- **PixelStreaming2HMD** (Runtime)  
  - Role: HMD pose/input handling in streamed sessions.
- **PixelStreaming2Input** (Runtime)  
  - Role: Routes WebRTC input events back to the engine.

## 4. Important Types & APIs
- Core interfaces (PixelStreaming2Core/Public):  
  - `IPixelStreaming2VideoProducer`, `IPixelStreaming2VideoConsumer`, `IPixelStreaming2VideoSink` for video pipeline stages.  
  - `IPixelStreaming2AudioProducer`, `IPixelStreaming2AudioConsumer`, `IPixelStreaming2AudioSink` for audio pipeline stages.  
  - `IPixelStreaming2Streamer` to manage a streaming session.  
- Utilities: `PixelStreaming2Utils`, `PixelStreaming2Delegates` for helper functions and event hooks.
- (Other modules build on these interfaces; detailed implementations reside in private source.)

## 5. Typical usage patterns
- Enable the plugin with required dependencies (`PixelCapture`, codecs, WebSocketNetworking, MediaIOFramework).  
  - Target platforms exclude Win64 ARM64 (denied in the `.uplugin`).  
- Configure streaming settings via `PixelStreaming2Settings`.  
- Implement or use provided producers/consumers to feed video/audio into a streamer, then start signalling/transport through the RTC module.  
- Use the input module to forward WebRTC input back into UE; HMD module supports XR pose/input streaming.

## 6. Version-specific notes (UE 5.7)
- Not marked experimental, but new modular architecture compared to Pixel Streaming v1.  
- No explicit 5.7-only changes documented; overview reflects current source.

