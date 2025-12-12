# XRScribe Plugin Overview

## 1. What this plugin does
- Experimental OpenXR API capture and emulation layer for debugging XR sessions.
- Records OpenXR calls to a file via a capture layer and can replay them through an emulation layer.
- Provides developer settings and utilities for serializing/deserializing captured API traffic and pose data.
- Targeted at Win64; disabled by default.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Developer-facing OpenXR capture/emulation layer with configurable settings for recording and replaying XR sessions without hardware.

## 3. Key Modules
- **XRScribe** (Runtime, Win64): Implements the capture/emulation layers, serialization, and developer settings.

## 4. Important Types & APIs
- `FXRScribeAPILayer`: Base layer that hooks into the OpenXR loader to intercept API calls.
- `FXRScribeCaptureLayer`: Captures OpenXR function traffic and serializes it via `FXRScribeAPIEncoder` into the XRScribe file format.
- `FXRScribeEmulationLayer`: Replays captured calls using `FXRScribeAPIDecoder`, driving emulated state for testing without hardware.
- `FXRScribeAPIEncoder` / `FXRScribeAPIDecoder`: Translate OpenXR structures and commands to/from the on-disk `XRScribe` file format.
- `FXRScribeEmulatedPoseManager`: Manages pose timelines used during emulation/replay.
- `UXRScribeDeveloperSettings`: Configurable developer settings for capture/emulation behavior.

## 5. Typical usage patterns
- Enable alongside OpenXR to insert the XRScribe layer into the OpenXR loader chain.
- Use capture mode to record OpenXR sessions; serialized files contain API calls and pose data.
- Switch to emulation mode to replay captured sessions without a connected device, leveraging the emulated pose manager.
- Tune capture paths and behavior through `UXRScribeDeveloperSettings`.

## 6. Version-specific notes (UE 5.7)
- Marked experimental and Win64-only; no additional UE 5.7-specific notes.

