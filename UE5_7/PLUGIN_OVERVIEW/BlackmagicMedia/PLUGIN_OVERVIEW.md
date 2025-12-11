# Blackmagic Media Player Plugin Overview

## 1. What this plugin does

- Provides video/audio input and output using Blackmagic capture/output cards.
- Adds media sources, media outputs, timecode providers, and custom time step support tailored to Blackmagic hardware.
- Includes editor tooling and factories to create and configure Blackmagic media assets.

## 2. Key Modules

- **BlackmagicCore** (Runtime) — Hardware interaction helpers, device discovery, platform shims.
- **BlackmagicMedia** (Runtime) — Media player implementation for ingesting from Blackmagic devices.
- **BlackmagicMediaOutput** (Runtime) — Media output path for sending frames/audio to hardware.
- **BlackmagicMediaFactory** (RuntimeNoCommandlet + Editor) — Registers media source/output asset types and factories.
- **BlackmagicMediaEditor** (Editor) — Editor customizations and UI for asset configuration.

## 3. Important Types & APIs

- Core/device helpers: `FBlackmagicDevice`, `FBlackmagicDeviceScanner`, `FBlackmagicInputChannel`, `FBlackmagicOutputChannel`, `FBlackmagicDeviceProvider`.
- Media ingest: `UBlackmagicMediaSource`, `UBlackmagicMediaCapture`, `FBlackmagicMediaPlayer`.
- Media output: `UBlackmagicMediaOutput`, `UBlackmagicMediaCapture`, `BlackmagicMediaOutput` runtime module classes.
- Timing: `UBlackmagicCustomTimeStep`, `UBlackmagicTimecodeProvider` for genlock/timecode sync.
- Factories and editor UI: `UBlackmagicMediaSourceFactoryNew`, `UBlackmagicMediaOutputFactoryNew`, plus module `BlackmagicMediaEditor` for details panels and tooling.

## 4. Typical usage patterns

- Enable the plugin, then create `Blackmagic Media Source` assets to capture SDI/HDMI feeds; assign them to Media Players or Media Framework utilities.
- For output, create a `Blackmagic Media Output` asset and attach it to a Media Output component or render pipeline to send frames to Blackmagic hardware.
- Configure timecode/genlock via `UBlackmagicCustomTimeStep` or `UBlackmagicTimecodeProvider` in Project Settings when synchronizing to house sync.
- Use the editor asset factories to select the target card, port, pixel format, and audio channels; runtime playback/capture is handled by the media framework.

## 5. Version-specific notes (UE 5.7)

- Disabled by default; intended for projects using Blackmagic hardware.
- No explicit UE 5.7-specific notes found; overview reflects the current plugin code.
