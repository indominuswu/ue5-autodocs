# WebM Media Plugin Overview

## 1. What this plugin does

- Implements a media player using the WebM container and VP codecs via third-party libraries.
- Provides audio/video decoders, container parsing, and media samples for playback.
- Supplies editor/import factory support for creating WebM media sources.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Media Framework integration for WebM with decoders and editor/import factories so users can create/play WebM media sources.

## 3. Key Modules

- **WebMMedia** (RuntimeNoCommandlet)
  - Role: Core playback implementation, container parsing, and sample sinks for WebM on Win64/Linux/Mac.
- **WebMMediaEditor** (Editor)
  - Role: Editor integration for WebM media assets and preview tooling.
- **WebMMediaFactory** (RuntimeNoCommandlet + Editor)
  - Role: Factory classes to import/create WebM media sources; runtime support registers factories on allowed platforms.

## 4. Important Types & APIs

### `IWebMMediaModule`
- Role: Module interface for WebM playback initialization.

### `FWebMContainer`
- Role: Parses WebM containers and exposes stream metadata to decoders.

### `FWebMAudioDecoder` / `FWebMVideoDecoder`
- Role: Decode WebM audio/video streams into engine-friendly sample formats.

### `FWebMMediaAudioSample` / `FWebMMediaTextureSample`
- Role: Media framework sample types used by the player for audio and video frames.

### `FWebMSamplesSink`
- Role: Receives decoded frames and feeds them into the media player pipeline.

## 5. Typical usage patterns

- Enable the plugin (desktop platforms). Import or reference a WebM media file; the factory registers the source for media playback.
- Use standard Media Framework components (MediaPlayer/MediaTexture) to play WebM sources; decoding is handled by `WebMMedia`.
- In the editor, use WebM-specific factories to create assets and preview playback; runtime module supplies decoding.

## 6. Version-specific notes (UE 5.7)

- Plugin is flagged beta. No additional UE 5.7-specific changes were identified.

