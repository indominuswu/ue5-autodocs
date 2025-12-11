# LiveLinkInputDevice Plugin Overview

## 1. What this plugin does
- Streams values from Unreal input devices (e.g., game controllers) as LiveLink subjects.
- Provides UI and settings to configure which input device data is published over LiveLink.

## 2. Key Modules
- **LiveLinkInputDevice** (Runtime)  
  - Role: LiveLink source for input device data.
  - Notable types: `ULiveLinkInputDeviceSourceFactory`, `ULiveLinkInputDeviceSourceSettings`, `ULiveLinkInputDeviceConnectionSettings`, `SLiveLinkInputDeviceSourceFactory`.

## 3. Important Types & APIs

### Source setup
- `ULiveLinkInputDeviceSourceFactory`: Adds a LiveLink source menu entry and builds the creation panel.
- `ULiveLinkInputDeviceConnectionSettings`: Captures device selection/configuration for creating the source.
- `ULiveLinkInputDeviceSourceSettings`: Source settings used after creation.

## 4. Typical usage patterns
- LiveLink panel: Add a new source via LiveLink, choose Input Device, and configure device-specific settings in the creation panel.
- Runtime/editor: Consume the resulting LiveLink subjects to drive animation or logic with controller inputs exposed through the LiveLink pipeline.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; plugin is disabled by default and primarily aimed at tooling/testing scenarios.

