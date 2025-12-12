# Web Socket Messaging Plugin Overview

## 1. What this plugin does

- Adds a WebSocket-based transport layer to the Unreal messaging subsystem for inter-process/device messaging.
- Supports running a messaging server/client over WebSockets on Win64/Mac/Linux.

## 2. Editor/Runtime surfaces

- User-facing: No - Messaging transport backend over WebSockets; minimal API beyond module status helpers, no gameplay/editor-facing functionality.

## 3. Key Modules

- **WebSocketMessaging** (Runtime)
  - Role: Implements the messaging transport using WebSockets and exposes module status helpers; depends on `DiscoveryBeaconReceiver` and `WebSocketNetworking`.

## 4. Important Types & APIs

### `IWebSocketMessagingModule`
- Role: Module interface providing `IsTransportRunning()` and `GetServerPort()` to introspect the active WebSocket messaging transport.

## 5. Typical usage patterns

- Enable the plugin along with `WebSocketNetworking`. Configure the messaging settings to use the WebSocket transport (and optionally discovery via beacon receiver).
- Query `IWebSocketMessagingModule` to check transport status or to retrieve the configured server port for diagnostics.

## 6. Version-specific notes (UE 5.7)

- Plugin is experimental. No additional UE 5.7-specific behaviors were observed in the source.

