# Remote Control Protocol OSC Plugin Overview

## 1. What this plugin does
- Enables Open Sound Control (OSC) messages to drive Remote Control presets.
- Hosts one or more OSC servers configured via project settings for receiving OSC commands.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Remote Control protocol with project settings (`URemoteControlProtocolOSCSettings`) to spin up OSC servers and bind OSC messages to exposed entities.

## 3. Key Modules
- **RemoteControlProtocolOSC** (Runtime)  
  - OSC protocol implementation that binds OSC messages to Remote Control protocol entities and dispatches updates to presets.

## 4. Important Types & APIs
### `URemoteControlProtocolOSCSettings` (Config=Engine)
- Role: Stores OSC server endpoints; initializes servers on load.
- Key property: `ServersSettings` array of `FRemoteControlOSCServerSettings` (each has `ServerAddress` in `IP:Port` format and an owning `UOSCServer`).
- Editor hook: `PostEditChangeProperty` reinitializes servers when settings change.

### `FRemoteControlOSCServerSettings`
- Role: Holds per-server address/port and handles server startup (`InitOSCServer`).

## 5. Typical usage patterns
- Enable Remote Control and this protocol.
- Set OSC server addresses/ports in Project Settings > Plugins > Remote Control > OSC.
- In the Remote Control Panel, choose OSC as the protocol for exposed entities; map OSC addresses to entity paths.
- Send OSC messages to the configured server(s); received values propagate to exposed properties or controllers.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.



