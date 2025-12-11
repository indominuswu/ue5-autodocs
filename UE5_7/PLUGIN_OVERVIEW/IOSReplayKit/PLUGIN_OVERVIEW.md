# ReplayKit for iOS Plugin Overview

## 1. What this plugin does

- Integrates Apple ReplayKit for local recording and broadcast capture on iOS.
- Exposes Blueprint nodes to start/stop recording or capture to file with microphone support.
- Includes UPL (iOSReplayKit_UPL.xml) to inject required platform settings when packaging.

## 2. Key Modules

- **IOSReplayKit** (Runtime, PreDefault) — ReplayKit bindings, platform glue, and Blueprint API.

## 3. Important Types & APIs

### `UIOSReplayKitControl` (UBlueprintFunctionLibrary)

- Role: Blueprint entry points for ReplayKit control.
- Key functions: `StartRecording`, `StopRecording`, `StartCaptureToFile`, `StopCapture`, each with optional microphone capture.

### Runtime helpers

- `ReplayKitRecorder` implements the underlying iOS recording logic; invoked by the Blueprint functions.

## 4. Typical usage patterns

- Enable the plugin for iOS. In Blueprints, call `StartRecording`/`StopRecording` for regular ReplayKit recording or `StartCaptureToFile`/`StopCapture` for direct file capture.
- Packaging uses the provided UPL to add required entitlements/Info.plist entries.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific changes found; feature set matches the current source with ReplayKit bindings.

