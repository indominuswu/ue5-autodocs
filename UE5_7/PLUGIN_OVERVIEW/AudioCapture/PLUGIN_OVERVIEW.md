# Audio Capture Plugin Overview

## 1. What this plugin does

- Provides microphone capture support for the Unreal audio engine.
- Exposes Blueprint and component APIs to start/stop capture and route incoming audio to submixes.
- Includes basic editor integration for configuring capture sources.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime component (`UAudioCaptureComponent`) and Blueprint libraries for developers to capture microphone input.

## 3. Key Modules

- **AudioCapture** (Runtime)  
  - Role: Core microphone capture implementation, components, and Blueprint nodes.
- **AudioCaptureEditor** (UncookedOnly)  
  - Role: Editor hooks for configuring capture devices and preview behavior.

## 4. Important Types & APIs

### `UAudioCaptureComponent` (USynthComponent)

- Role: Component that captures microphone input and outputs it as a procedural synth source.
- Key properties: Capture device selection, sound wave output routing.
- Key functions: Start/stop capture and connect to target submixes.

### `UAudioCaptureBlueprintLibrary`

- Role: Blueprint function library for starting capture and querying device info at runtime.
- Key functions: Open/close capture streams, get device capabilities.

### `UAudioCaptureFunctionLibrary`

- Role: Additional Blueprint helpers for managing capture devices and retrieving status.

## 5. Typical usage patterns

- Enable the plugin (on by default in many templates).
- Add `AudioCaptureComponent` to an actor, choose a capture device, and route output to a submix.
- Use Blueprint nodes from `AudioCaptureBlueprintLibrary`/`AudioCaptureFunctionLibrary` to start and stop capture or enumerate devices.
- For timecode-aware capture pipelines, pair with `AudioCaptureTimecodeProvider`.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

