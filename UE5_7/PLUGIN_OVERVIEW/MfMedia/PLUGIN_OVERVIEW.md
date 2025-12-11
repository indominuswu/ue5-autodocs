# Media Foundation Media Player Plugin Overview

## 1. What this plugin does

- Implements a Media Foundation-based media player for Windows and Xbox targets (Win7+).
- Adds an Electra-compatible playback path for audio/video streams using Microsoft’s MF pipeline.
- Provides editor factories so Media Player assets can instantiate the MF-backed player.
- Disabled by default; enable when targeting supported platforms that require MF decoding.

## 2. Key Modules

- **MfMedia** (RuntimeNoCommandlet) — core playback implementation, source reader sinks, sample/track handling (`FMfMediaPlayer`, `FMfMediaTracks`, `FMfMediaAudioSample`, `FMfMediaTextureSample`).
- **MfMediaFactory** (RuntimeNoCommandlet + Editor) — registers the Media Foundation player factory so `UMediaPlayer` can choose this backend.
- **MfMediaEditor** (Editor) — editor-only helpers and hooks for integrating the MF player in asset workflows.

## 3. Important Types & APIs

- `FMfMediaPlayer` — drives MF playback, manages state and clocking for audio/video.
- `FMfMediaTracks` — enumerates and selects MF media tracks.
- `FMfMediaAudioSample`, `FMfMediaTextureSample` — sample wrappers feeding audio and texture outputs to UE’s media pipeline.
- `IMfMediaSourceReaderSink`, `FMfMediaByteStream` — bridge between UE IO and the MF source reader.

## 4. Typical usage patterns

- Enable the plugin, then create or edit a `Media Player` asset and select the Media Foundation player type (via MfMedia factory) for Windows/Xbox playback.
- Use with MF-supported container/codec formats; relies on platform codecs provided by the OS.
- Combine with `MediaTexture`/`MediaSoundComponent` for rendering and audio output like other media backends.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-only behaviors noted; functionality reflects the current MF-based implementation.

