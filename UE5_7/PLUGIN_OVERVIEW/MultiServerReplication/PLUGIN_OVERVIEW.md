# Multi-server Replication Plugin Overview

## 1. What this plugin does
- Provides tools to connect and replicate state across multiple dedicated UE server processes.
- Implements proxy/beacon networking helpers and GUID caching for multi-server topologies.
- Supplies configuration helpers for defining server counts and launch parameters.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Multiplayer teams instantiate `UMultiServerNode`/proxy beacons and configure `UMultiServerSettings` to coordinate multiple server processes at runtime.

## 3. Key Modules
- **MultiServerReplication** (Runtime)
  - Role: Core multi-server networking—proxy connections, GUID caches, net drivers, and node coordination.
  - Notable types: `UMultiServerNode`, `UMultiServerProxy`, proxy net drivers/GUID caches, `AMultiServerBeaconClient`, backend connection helpers.
- **MultiServerConfiguration** (Runtime)
  - Role: Config-only module for defining multi-server settings.
  - Notable types: `UMultiServerSettings`.

## 4. Important Types & APIs

### `UMultiServerNode`
- Role: Central object that connects multiple server processes via beacons; tracks peer addresses and connection state.
- Key APIs: `Create`/`RegisterServer`, `ParseCommandLineIntoCreateParams`, `AreAllServersConnected`.
- Key data: `FMultiServerNodeCreateParams` (peer IDs, listen ports, beacon class, callbacks).

### Proxy networking classes
- Role: Provide proxy connections and GUID caches when routing client traffic across servers.
- Notable classes: `UMultiServerProxy`, `FProxyNetGUIDCache`, `FProxyBackendNetGUIDCache`, backend net drivers/host objects.

### `AMultiServerBeaconClient` and related host/host object types
- Role: Beacon-based communication channel between servers; intended to be subclassed for project RPCs.

### `UMultiServerSettings`
- Role: Config object (Game.ini) for declaring total server count and launch parameters used by external launch scripts.

## 5. Typical usage patterns
- Enable the plugin in server builds that need clustered/multi-process gameplay.
- Create a `UMultiServerNode` at server startup (for example in a custom `AGameSession`) using `FMultiServerNodeCreateParams` to specify peer addresses and beacon class.
- Implement a subclass of `AMultiServerBeaconClient` for custom RPCs between servers; register callbacks via `FOnMultiServerConnected`.
- Use `UMultiServerSettings` to declare the expected number of servers when launching via multi-server scripts.

## 6. Version-specific notes (UE 5.7)
- Plugin is experimental/opt-in; no explicit UE 5.7-specific notes found in source comments.

