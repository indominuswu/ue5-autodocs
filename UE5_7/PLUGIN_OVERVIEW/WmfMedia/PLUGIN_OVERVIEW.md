# WMF Media Player Plugin Overview

## 1. What this plugin does

- Implements a media player using Windows Media Foundation (WMF) for audio/video playback.
- Provides hardware-accelerated video decoding helpers and codec interfaces for WMF streams.
- Includes editor and factory modules for creating WMF-backed media sources.

## 2. Key Modules

- **WmfMedia** (Runtime)
  - Role: Core WMF media player, codec registration, and runtime decoding (Win64, non-server).
- **WmfMediaEditor** (Editor)
  - Role: Editor integration for WMF media playback and tooling.
- **WmfMediaFactory** (RuntimeNoCommandlet + Editor)
  - Role: Factory for WMF media sources, registered for Win64/Mac/Linux targets (runtime factory allows cross-platform registration while WMF playback is Windows-focused).

## 3. Important Types & APIs

### `IWmfMediaModule`
- Role: Module interface controlling WMF media initialization.

### `FWmfMediaCodec` / `IWmfMediaCodec`
- Role: Codec abstraction for WMF streams; handles creation of WMF decoders.

### `FWmfMediaHardwareVideoDecoding*`
- Role: Helpers for hardware-accelerated video decoding (rendering, shaders, texture samples) on supported GPUs.

### `FWmfMediaCommon`
- Role: Shared types and utilities used by the WMF media player implementation.

## 4. Typical usage patterns

- Enabled by default on Win64. Create media sources/players as usual; WMF handles playback for compatible formats.
- Use MediaPlayer/MediaTexture components; WMF codec registration allows playback without extra setup. Editor module supports previewing WMF media.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific notes identified; plugin remains the default WMF-backed media path on Windows.
