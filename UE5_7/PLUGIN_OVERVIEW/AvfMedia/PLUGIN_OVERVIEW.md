# AVF Media Player Plugin Overview

## 1. What this plugin does

- Implements a media player using Apple AVFoundation for iOS, macOS, tvOS, and allowed Linux builds.
- Supports playback of audio/video with overlay, audio, and texture sampling paths tailored to Apple platforms.
- Provides optional media capture support through AVFoundation capture devices.
- Editor factories and settings integrate AVF playback into Unreal’s Media framework.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Media Framework backend with project settings (`UAvfMediaSettings`) and editor factories for AVFoundation playback/capture on Apple platforms.

## 3. Key Modules

- **AvfMedia** (RuntimeNoCommandlet, PreLoadingScreen)  
  - Role: Core AVFoundation media player implementation (player, tracks, sampling).
- **AvfMediaCapture** (RuntimeNoCommandlet)  
  - Role: Capture device handling for AVFoundation.
- **AvfMediaFactory** (RuntimeNoCommandlet + Editor)  
  - Role: Media source/player factories and platform registrations.
- **AvfMediaEditor** (Editor)  
  - Role: Editor hooks and assets for AVF playback.

## 4. Important Types & APIs

- `FAvfMediaPlayer`, `FAvfMediaTracks`, `FAvfMediaOverlaySample`, `FAvfMediaAudioSample`, `FAvfMediaTextureSample`, `FAvfMediaVideoSampler`: Core AVFoundation player and sampling classes.
- `UAvfMediaSettings`: Project settings for AVFoundation playback/capture behavior.
- `FAvfMediaCaptureHelper`, `FAvfMediaCapturePlayer`: Capture-specific helpers for ingesting frames from AVFoundation.
- `UAvfFileMediaSourceFactory`: Factory enabling AVF-backed media sources in the editor.
- Module interfaces `IAvfMediaModule`: Entry point for registering player support with the Media framework.

## 5. Typical usage patterns

- Enable the plugin on Apple platforms; AVF becomes an available media player option for `MediaSource` assets.
- Create or import media sources in the editor; the AVF factory registers AVFoundation as the playback backend.
- Configure `Project Settings -> Plugins -> AVF Media` via `UAvfMediaSettings` for platform-specific capture/playback preferences.
- For capture, use AVFoundation-compatible devices; frames are routed through `AvfMediaCapture` classes to Media pipelines.

## 6. Version-specific notes (UE 5.7)

- Enabled by default for supported Apple platforms.
- No explicit UE 5.7-specific notes found; this overview reflects the current plugin state.

