# Live Link Hub Unreal Device Plugin Overview

## 1. What this plugin does
- Implements a Live Link Hub device that connects directly to a running Unreal Editor instance.
- Handles Take Recorder automation events (start/stop) and connection state for the remote editor client.
- Exposes device settings so hub operators can target a specific editor client and control recording authority.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Live Link Hub users add an Unreal device, configure `ULiveLinkUnrealDeviceSettings`, and use it to connect to editor clients and drive recording commands.

## 3. Key Modules
- **LiveLinkUnrealDevice** (Editor)  
  - Device implementation and supporting messaging structures.  
  - Notable types: `ULiveLinkUnrealDevice`, `ULiveLinkUnrealDeviceSettings`, `LiveLinkUnrealDeviceMessages`, `LiveLinkHubUnrealDeviceAux`.

## 4. Important Types & APIs

### `ULiveLinkUnrealDeviceSettings`
- Role: Per-device settings (display name, target `FLiveLinkHubClientId`, recording authority flags) editable in hub UI.

### `ULiveLinkUnrealDevice`
- Role: `ULiveLinkDevice` subclass implementing connection and recording capabilities for communicating with Unreal Editor over the message bus.
- Key behavior: manages connection status, hardware ID, connect/disconnect commands, and propagates recording start/stop events; listens for message bus notifications and Take Recorder events.

### `LiveLinkUnrealDeviceMessages` / `LiveLinkHubUnrealDeviceAux`
- Role: Auxiliary message types and helpers for exchanging control messages between hub and editor clients.

## 5. Typical usage patterns
- Enable alongside Live Link Hub and Live Link Device Framework.
- In the hub device list, add an “Unreal” device and set `ClientId` to the target editor client; optionally allow the device to start/stop hub recording.
- Use the hub UI to connect/disconnect and monitor device health; recording commands will mirror to the connected editor for synchronized takes.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

