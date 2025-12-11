# Live Link Device Framework Plugin Overview

## 1. What this plugin does
- Supplies the base framework for implementing Live Link Hub devices inside Unreal Editor.
- Manages device lifecycle and capability discovery, allowing hub-aware devices to register, expose settings, and participate in session saving/loading.
- Provides Blueprint-facing subsystem APIs for enumerating and creating device instances.

## 2. Key Modules
- **LiveLinkDevice** (Editor)  
  - Editor module hosting the device subsystem and capability metadata.  
  - Notable types: `ULiveLinkDeviceSubsystem`, `ULiveLinkDevice`, `ULiveLinkDeviceSettings`, `ULiveLinkDeviceCapability`.

## 3. Important Types & APIs

### `ULiveLinkDeviceSubsystem`
- Role: `UEngineSubsystem` that owns all Live Link devices in the editor; registers device and capability classes, and handles session persistence through Live Link Hub extra data.
- Key APIs: `CreateDeviceOfClass`, `RemoveDevice`, `GetDevicesByClass`, `GetDevicesByCapability`, and delegates `OnDeviceAdded`/`OnDeviceRemoved`.

### `ULiveLinkDevice` / `ULiveLinkDeviceSettings`
- Role: Base device implementation and associated per-device settings; device classes expose connection/recording capabilities and respond to lifecycle events (`OnDeviceAdded`, `OnDeviceRemoved`, `OnSettingChanged`).

### `ULiveLinkDeviceCapability`
- Role: Marker interfaces for optional capabilities (e.g., connection state, recording control) used to populate hub UI and tables.

## 4. Typical usage patterns
- Enable the plugin in the editor (used by Live Link Hub and related device plugins).
- Create a custom `ULiveLinkDevice` subclass implementing desired capabilities; register it so `ULiveLinkDeviceSubsystem` can instantiate and track it.
- Use Blueprint or editor tooling to list devices (`GetDevicesByClass`/`GetDevicesByCapability`), respond to `OnDeviceAdded`/`OnDeviceRemoved`, and persist settings with hub sessions.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
