# Motion Design Data Link Plugin Overview

## 1. What this plugin does

- Provides a communication layer for motion design tools, supporting HTTP, JSON, data tables, and WebSocket transports.
- Supplies runtime subsystems for managing connections and data exchange, plus editor support for graph authoring.
- Forms part of the virtual production tooling stack.

## 2. Key Modules

- **DataLink** (Runtime)  
  - Role: Core runtime features; entry point for shared definitions.
- **DataLinkHttp** (Runtime)  
  - Role: HTTP transport support and settings builders.
- **DataLinkJson** (Runtime)  
  - Role: JSON payload handling helpers.
- **DataLinkDataTable** (Runtime)  
  - Role: Data table integration for Data Link sources/targets.
- **DataLinkWebSocket** (Runtime)  
  - Role: WebSocket transport management.
  - Notable types: `UDataLinkWebSocketSubsystem`.
- **DataLinkEdGraph** (UncookedOnly)  
  - Role: Editor graph schema for configuring data link flows.
- **DataLinkEditor** (Editor)  
  - Role: Editor UI and asset customizations.
- **DataLinkJsonEditor** (Editor)  
  - Role: JSON-specific editor helpers.

## 3. Important Types & APIs

### `UDataLinkWebSocketSubsystem`
- Role: Engine subsystem managing WebSocket connections identified by handles.
- Key functions: `CreateWebSocket`, `CloseWebSocket`, `FindWebSocket`, internal cleanup of invalid sockets.

### HTTP/JSON helpers
- Role: Settings builders (`DataLinkNodeHttpSettingsBuilder`) and JSON translators for runtime data exchange.
- Key behavior: Provide configuration objects and serialization helpers for Data Link nodes.

## 4. Typical usage patterns

- Enable the plugin for virtual production or motion design projects that require live data transport.
- Use the editor graph modules to configure Data Link flows, selecting HTTP/JSON/WebSocket transports as needed.
- At runtime, create or retrieve connections via `UDataLinkWebSocketSubsystem` or the HTTP settings builders, then push/pull payloads through configured nodes.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-only notes; plugin ships in this branch with multiple runtime/editor modules enabled by default states defined in the .uplugin.
