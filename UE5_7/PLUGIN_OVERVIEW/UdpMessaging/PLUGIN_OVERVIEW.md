# UDP Messaging Plugin Overview

## 1. What this plugin does

- Provides a UDP-based transport and optional tunnel layer for the engine messaging framework, enabling discovery and message exchange across machines and devices.
- Supports multicast and unicast endpoints plus static endpoint lists for cross-subnet communication.
- Offers configurable reliability, send rate limiting, auto-repair, and endpoint blocking to adapt to different network conditions.
- Can expose tunnel endpoints to bridge traffic between otherwise disconnected networks.

## 2. Key Modules

- **UdpMessaging** (RuntimeAndProgram)  
  - Role: Implements the UDP message transport and tunnel provider used by the engine messaging system in editor, games, and tools.  
  - Notable types: `UUdpMessagingSettings`.

## 3. Important Types & APIs

### `UUdpMessagingSettings`

- Role: Project settings controlling how UDP messaging binds, broadcasts, and tunnels traffic. Configurable via `DefaultEngine.ini` or the Project Settings UI.
- Key properties:
  - `EnabledByDefault`, `EnableTransport`, `EnableTunnel`, `bAutoRepair`, `AutoRepairAttemptLimit` to govern activation and resiliency.
  - `UnicastEndpoint`, `MulticastEndpoint`, `MulticastTimeToLive`, `StaticEndpoints`, `ExcludedEndpoints`, `ReliableQueuePriority`, `WorkQueueSize`, `MaxSendRate`, `MaxConcurrentDeserializationTasks`, `ConnectionTimeoutPeriod` to tune transport behavior.
  - Tunnel-specific `TunnelUnicastEndpoint`, `TunnelMulticastEndpoint`, `RemoteTunnelEndpoints` for bridging networks.
  - `MessageFormat` to choose CBOR endianness used to serialize payloads.

## 4. Typical usage patterns

- Enable the plugin, then configure endpoints under Project Settings → Plugins → UDP Messaging (or via `DefaultEngine.ini`). Common flags: `-messaging` and `-UDPMESSAGING_TRANSPORT_ENABLE=` on the command line for non-editor builds.
- Set `UnicastEndpoint`/`MulticastEndpoint` to match your network and add `StaticEndpoints` for peers on other subnets. Adjust `MaxSendRate` and reliability settings if you see packet loss.
- Enable the tunnel if you need to bridge disparate networks; populate `RemoteTunnelEndpoints` for the tunnel mesh.
- The transport is used automatically by the engine messaging bus (e.g., Session Frontend, Remote Control, Multi-User); no direct code changes are required beyond settings.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
