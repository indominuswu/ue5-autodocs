# AJA Media Player Plugin Overview

## 1. What this plugin does
- Implements media input/output support for AJA capture cards.
- Provides media source, output, and capture classes along with factory/editor integrations.
- Supports timecode, audio/video sample handling, and Electra frame grabbing paths.

## 2. Key Modules
- **AjaCore** (Runtime)
  - Role: Low-level device/channel management and synchronization for AJA hardware.
- **AjaMedia** (Runtime)
  - Role: Media player/capture implementation using AJA devices.
- **AjaMediaOutput** (Runtime)
  - Role: Media output/capture pipeline (frame grabber, capture object).
- **AjaMediaFactory** (Editor + RuntimeNoCommandlet)
  - Role: Asset factories for AJA media sources/outputs.
- **AjaMediaEditor** (Editor)
  - Role: Editor customizations (e.g., timecode reference customization) and asset tooling.

## 3. Important Types & APIs

### `UAjaMediaSource`
- Role: Describes an AJA input source (device, channel, timecode reference); used to create media players.

### `UAjaMediaOutput` / `UAjaMediaCapture`
- Role: Configure AJA output channels and drive frame capture to device outputs.

### `FAjaMediaPlayer`
- Role: Media player handling audio/video sample acquisition and presentation from AJA input.

### Settings & factories
- `UAjaMediaSettings` project-level defaults; `UAjaMediaSourceFactoryNew` and `UAjaMediaOutputFactoryNew` create assets.

## 4. Typical usage patterns
- Create an `UAjaMediaSource` asset, set device/channel/timecode, and play it through a Media Player.
- For output, create an `UAjaMediaOutput` and use `UAjaMediaCapture` to send render targets out via AJA hardware.
- Configure defaults in `Project Settings > Plugins > AJA Media`; use editor customizations for timecode/reference.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.