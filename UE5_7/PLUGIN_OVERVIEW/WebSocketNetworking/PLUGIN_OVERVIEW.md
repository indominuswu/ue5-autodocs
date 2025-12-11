# Experimental WebSocket Networking Plugin Overview

## 1. What this plugin does

- Implements a WebSocket-based network driver and server for Unreal networking.
- Provides connection/server interfaces and delegates for WebSocket events, targeting desktop platforms.
- Intended for experimental HTML5/WebSocket-style networking scenarios.

## 2. Key Modules

- **WebSocketNetworking** (Runtime)
  - Role: Supplies the `WebSocketNetDriver`, connection layer, server interfaces, and delegates for WebSocket transport.

## 3. Important Types & APIs

### `IWebSocketNetworkingModule`
- Role: Module interface for initialization and availability checks.

### `IWebSocketServer`
- Role: Interface for hosting a WebSocket server to accept connections.

### `FWebSocketConnection`
- Role: Represents a single WebSocket connection used by the net driver.

### `WebSocketNetworkingDelegates.h`
- Role: Delegate definitions for connection events and messaging callbacks.

### `WebSocketNetDriver`
- Role: Network driver implementation enabling Unreal networking over WebSockets (requires disabling conflicting NetDriver definitions and unsupported packet handlers as noted in the plugin description).

## 4. Typical usage patterns

- Enable the plugin (Win64/Mac/Linux). Configure project NetDriver settings to use `WebSocketNetDriver` and disable other NetDriverDefinitions/unsupported PackHandlerComponents per plugin notes.
- Use `IWebSocketServer`/`WebSocketNetworkingDelegates` to host a WebSocket server or manage connections.
- Pair with `WebSocketMessaging` for messaging-layer transport if needed.

## 5. Version-specific notes (UE 5.7)

- Plugin is experimental. No explicit UE 5.7-only changes were noted.
