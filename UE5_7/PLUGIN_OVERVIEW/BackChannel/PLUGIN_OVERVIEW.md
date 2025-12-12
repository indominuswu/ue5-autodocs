# BackChannel Plugin Overview

## 1. What this plugin does

- Experimental runtime channel for external tools/apps to query and push data into a running Unreal session.
- Provides lightweight socket-based connections plus OSC (Open Sound Control) helpers for structured messaging.
- No editor UI; intended for programmatic integration and tooling.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime networking/OSC API (`IBackChannelSocketConnection`, `FBackChannelOSCConnection`, `FDispatchMap`) for developers integrating external control channels.

## 3. Key Modules

- **BackChannel** (RuntimeNoCommandlet)  
  - Role: Core connection, packet, transport, and OSC messaging utilities.

## 4. Important Types & APIs

- `IBackChannelConnection`, `IBackChannelSocketConnection`: Interfaces for network connections and transport abstraction.
- `IBackChannelPacket`, `FBackChannelCommon::FBackChannelOSCPacket`: Packet format helpers for sending/receiving data.
- OSC helpers: `FBackChannelOSCMessage`, `FBackChannelOSCBundle`, `FBackChannelOSCConnection`, `FBackChannelOSCPacket`.
- `FBackChannelThreadedConnection`: Threaded connection wrapper to handle async traffic.
- `FDispatchMap`: Utility for routing received packets/OSC messages to handlers.

## 5. Typical usage patterns

- Enable the plugin and add `BackChannel` as a module dependency in your game/plugin module.
- Create a `IBackChannelSocketConnection` to open a TCP/UDP channel, then wrap it with `FBackChannelOSCConnection` to exchange OSC messages.
- Register message handlers via `FDispatchMap` to respond to incoming commands from external tools.
- Use threaded connections when high-frequency or blocking I/O is expected.

## 6. Version-specific notes (UE 5.7)

- Marked experimental and enabled by default in UE 5.7.
- No additional UE 5.7-specific notes found.

