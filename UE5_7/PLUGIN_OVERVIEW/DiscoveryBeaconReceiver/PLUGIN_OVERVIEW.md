# Discovery Beacon Receiver Plugin Overview

## 1. What this plugin does

- Listens on a multicast socket for discovery beacons and responds with engine information.
- Allows external tools to discover running Unreal instances on the local network.
- Provides a base receiver implementation that can be specialized for different protocols.

## 2. Key Modules

- **DiscoveryBeaconReceiver** (Runtime) – Socket listener, threading, and protocol handling for discovery beacons.

## 3. Important Types & APIs

- `FDiscoveryBeaconReceiver` – Runnable base class that opens a multicast socket, receives beacon messages, and replies with connection info. Override `GetDiscoveryAddress`, `GetDiscoveryPort`, and `MakeBeaconResponse` to implement protocol-specific behavior.
- `FDiscoveryBeaconReceiverModule` – Module interface to start/stop the receiver at runtime.

## 4. Typical usage patterns

- Enable the plugin in tools that need to auto-detect Unreal editor or game instances.
- Instantiate a subclass of `FDiscoveryBeaconReceiver` (or configure an existing one) to listen on the desired address/port and craft the response data.
- Start the receiver via `Startup()`, allow it to run on its worker thread, and call `Shutdown()` when discovery is no longer required.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
