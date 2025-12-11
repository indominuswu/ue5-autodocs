# Epic Stage App Plugin Overview

## 1. What this plugin does
- Exposes a remote-control endpoint so the external Epic Stage App can discover and talk to an engine instance.
- Relies on nDisplay and Remote Control to drive stage playback and configuration remotely.
- Handles beacon-based discovery and lightweight request/response routing for the companion app.

## 2. Key Modules
- **EpicStageApp** (Runtime)
  - Role: Runtime support for discovery beacons, request routing, and app-facing helpers.
  - Notable types: `UStageAppFunctionLibrary`, `UStageAppSettings`, `FStageAppRouteHandler`, `FStageAppBeaconReceiver`.

## 3. Important Types & APIs

### `UStageAppFunctionLibrary`
- Role: Blueprint helpers for the Stage App integration.
- Key functions: `GetAPIVersion()` for the semantic API version, `GetRemoteControlWebInterfacePort()` for the exposed HTTP port.

### `UStageAppSettings`
- Role: Project-level developer settings surfaced under Plugins → Epic Stage App.
- Key properties: `DiscoveryEndpoint` multicast address, `DiscoveryPort` for beacon listen, legacy `DiscoverySocketWaitTime` (deprecated, no longer used).

### `FStageAppRouteHandler` and request/response structs
- Role: Internal routing for HTTP/JSON requests coming from the Stage App and formatting responses.
- Works with `FStageAppRequest`/`FStageAppResponse` to exchange payloads safely.

### `FStageAppBeaconReceiver`
- Role: Listens for discovery beacons so the Stage App can locate running editor instances on the LAN.
- Exposes callbacks to notify when a stage endpoint is found.

## 4. Typical usage patterns
- Enable Epic Stage App along with Remote Control and nDisplay, then configure `Project Settings → Plugins → Epic Stage App` for the multicast endpoint and port.
- Start the editor or packaged build; the beacon receiver advertises the instance and the Stage App can connect over the reported Remote Control port.
- Use the Blueprint function library in test levels to verify connectivity or surface the API version for diagnostics.

## 5. Version-specific notes (UE 5.7)
- The settings still include deprecated `DiscoverySocketWaitTime`; otherwise no explicit UE 5.7-only behaviors were identified. This overview reflects the current 5.7 source.
