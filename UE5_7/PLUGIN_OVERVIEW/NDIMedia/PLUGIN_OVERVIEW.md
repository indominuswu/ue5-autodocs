# NDI Media Plugin Overview

## 1. What this plugin does

- Provides NDI-based media source, output, and capture integration for UE’s Media Framework.
- Streams video, audio, ancillary data, and timecode over the NDI protocol.
- Supplies project-wide NDI settings plus Blueprint-friendly assets for ingest and playout.
- Includes editor factories/customizations for creating NDI media assets.

## 2. Key Modules

- **NDIMedia** (Runtime) – Core NDI media source/output, receiver management, capture/timecode provider support.
- **NDIMediaRendering** (Runtime) – Shader/conversion support for NDI texture samples and GPU paths.
- **NDIMediaEditor** (Editor) – Asset factories, asset definitions, and settings customization for NDI sources/outputs.

## 3. Important Types & APIs

### `UNDIMediaSource`

- Media source for NDI streams derived from `UCaptureCardMediaSource`.
- Key properties: `MediaConfiguration` (device/port/video format), `Bandwidth`, per-stream capture toggles (`bCaptureVideo`, `bCaptureAudio`, `bCaptureAncillary`) with buffer sizes, `bSyncTimecodeToSource`.

### `UNDIMediaOutput`

- Describes an NDI target used with Media Capture to send rendered output over NDI.
- Configures connection settings and pixel format/output device selection (via `FNDIMediaOutputOptions` and related structures).

### `UNDIMediaCapture`

- Capture implementation that pairs with `UNDIMediaOutput` to push frames/audio/ancillary data to NDI senders.

### `UNDIMediaSettings`

- Project settings for NDI transport (connection discovery, default bandwidth, timecode sync options).

### `UNDIMediaTimecodeProvider`

- Timecode provider that reads NDI timecode from an input stream for engine synchronization.

## 4. Typical usage patterns

- Enable the plugin, then create `NDI Media Source` assets (factory in the Media section) to describe inbound streams; set bandwidth and capture toggles per source.
- Use a `Media Player` + `Media Texture/Media Sound` with an `UNDIMediaSource` to preview NDI inputs; optional `UNDIMediaTimecodeProvider` can drive the engine timecode.
- For output, create an `NDI Media Output` asset and assign it to a `Media Capture` component or viewport capture; configure ancillary/audio/video buffers as needed.
- Editor integration exposes NDI settings in Project Settings and provides asset actions/factories for sources and outputs.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

