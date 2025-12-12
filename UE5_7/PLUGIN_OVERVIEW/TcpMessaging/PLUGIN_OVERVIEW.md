# TCP Messaging Plugin Overview

## 1. What this plugin does
- Adds a TCP-based message transport layer for the engine’s messaging subsystem.
- Supports sending/receiving messages between networked machines via configurable TCP endpoints.
- Available to select tools (UnrealFrontend, UnrealInsights, UnrealPak) as well as games when enabled.

## 2. Editor/Runtime surfaces

- User-facing: No - Transport-layer backend configured via ini (`UTcpMessagingSettings`); no editor UI or gameplay-level features beyond messaging infrastructure.

## 3. Key Modules
- **TcpMessaging** (Runtime, PreDefault) – TCP message transport implementation and configuration.

## 4. Important Types & APIs
- `UTcpMessagingSettings` (`UObject` config) – Holds transport enable flag, listen endpoint, connect-to endpoints, retry delays/periods, and whether to stop service when app deactivates.
- `FTcpMessageTransport` (Transport) – Implements the messaging transport over sockets, using the configured endpoints and socket subsystem.

## 5. Typical usage patterns
- Enable the plugin and configure `DefaultEngine.ini` (Engine section) for `EnableTransport`, `ListenEndpoint`, and `ConnectToEndpoints`.
- Use for editor tools or runtime builds that need cross-machine message bus connectivity; reconnect behavior is controlled by retry settings.
- Optionally stop the transport when the application deactivates via settings.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; plugin remains stable and enabled by default.

