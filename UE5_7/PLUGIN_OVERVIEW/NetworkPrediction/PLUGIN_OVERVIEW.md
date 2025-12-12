# Network Prediction Plugin Overview

## 1. What this plugin does

- Implements a generalized simulation framework for network-predicted gameplay systems.
- Provides replication proxies, buffering, rollback, and fixed/independent ticking models for deterministically simulated actors.
- Exposes components and subsystem helpers to wire simulations into actor replication and input production.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Developers build gameplay simulations on `UNetworkPredictionComponent`/`UNetworkPredictionWorldManager`, configuring replication proxies and tick models for their actors.

## 3. Key Modules

- **NetworkPrediction** (Runtime) – Core framework (proxies, world subsystem, replication integration, config/settings, debug/tracing helpers).

## 4. Important Types & APIs

### `UNetworkPredictionWorldManager`

- `UWorldSubsystem` that owns registered simulations, tick scheduling, replication bindings, and config/state tracing.
- Creates simulation IDs, binds network send/recv delegates, and manages service configuration.

### `UNetworkPredictionComponent`

- Abstract `UActorComponent` base that hosts a simulation via `FNetworkPredictionProxy`; handles replication hooks and RPC bridging (`ServerReceiveClientInput`).
- Derived components initialize the proxy in `InitializeNetworkPredictionProxy` to register their simulation.

### `FNetworkPredictionProxy` / `FReplicationProxy` / `FNetworkPredictionInstanceConfig`

- Core data structures that pair simulations with replication state and configure ticking policies, buffers, and network roles.

### Debug and tracing helpers

- APIs in `NetworkPredictionTrace`, `NetworkPredictionDebug`, and `NetworkPredictionUtil` expose trace channels and validation helpers for simulations.

## 5. Typical usage patterns

- Derive a component from `UNetworkPredictionComponent`, implement `InitializeNetworkPredictionProxy`, and register a simulation model/driver with `UNetworkPredictionWorldManager`.
- Use replication proxies to serialize input/sync/aux state; choose fixed or independent ticking via config.
- For debugging, enable trace capture to inspect simulation timelines and corrections.

## 6. Version-specific notes (UE 5.7)

- No UE 5.7-specific flags found; the framework reflects the shipped 5.7 source.

