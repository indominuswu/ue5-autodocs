# Audio Capture Timecode Provider Plugin Overview

## 1. What this plugin does

- Decodes LTC (linear timecode) from a live audio capture device (e.g., line-in) to drive engine timecode.
- Intended for synchronization with external audio/video hardware that embeds timecode on an audio channel.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Selectable timecode provider that reads LTC from audio capture devices for synchronization workflows.

## 3. Key Modules

- **AudioCaptureTimecodeProvider** (Runtime)  
  - Role: Implements a timecode provider that reads LTC from an audio capture stream.

## 4. Important Types & APIs

- The module exposes the engine timecode provider implementation; no public subsystems or components were identified in headers. Configuration is driven through project timecode provider settings.

## 5. Typical usage patterns

- Enable the plugin and select the Audio Capture Timecode Provider in Project Settings > Engine > Timecode Provider.
- Choose the audio input device carrying LTC; start play to have engine timecode follow the decoded LTC signal.
- Often paired with `AudioCapture` for device enumeration and capture setup.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

