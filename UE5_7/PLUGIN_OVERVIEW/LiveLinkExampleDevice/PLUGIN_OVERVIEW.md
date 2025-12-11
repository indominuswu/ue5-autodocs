# Live Link Hub Example Device Plugin Overview

## 1. What this plugin does
- Demonstrates how to implement a Live Link Hub device using the Live Link Device framework.
- Provides a simple device with connection/recording capabilities and editable network settings.
- Intended as a reference/sample for building custom devices that talk to Live Link Hub.

## 2. Key Modules
- **LiveLinkExampleDevice** (Editor)  
  - Example implementation of `ULiveLinkDevice` plus capabilities.  
  - Notable types: `ULiveLinkExampleDevice`, `ULiveLinkExampleDeviceSettings`.

## 3. Important Types & APIs

### `ULiveLinkExampleDeviceSettings`
- Role: Configurable settings for the sample device (display name, IP address, port) exposed in the editor device UI.

### `ULiveLinkExampleDevice`
- Role: Sample device deriving from `ULiveLinkDevice` and implementing `ILiveLinkDeviceCapability_Connection` and `ILiveLinkDeviceCapability_Recording`.
- Key behavior: overrides `OnDeviceAdded/Removed` and `OnSettingChanged`, provides connection status, hardware ID, connect/disconnect, and start/stop recording implementations; tracks connection state and recording flag internally.

## 4. Typical usage patterns
- Enable alongside Live Link Hub and Live Link Device Framework.
- Add the sample device through the hub UI; edit `DisplayName`, `IpAddress`, and `Port` in `ULiveLinkExampleDeviceSettings`, then use connect/record controls to exercise the capability hooks.
- Use as a reference template when authoring your own device plugin (copy the settings/device classes and adapt connection/recording logic).

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
