# DMX DisplayCluster Plugin Overview

## 1. What this plugin does

- Integrates DMX data with nDisplay light cards for virtual production workflows.
- Provides a DMX-enabled light card component and a replicator that maps incoming DMX buffers to light card parameters.
- Enables real-time DMX control of nDisplay light cards across the cluster.

## 2. Key Modules

- **DMXDisplayCluster** (Runtime) – Core integration between DMX streams and nDisplay light cards, including replication logic.
- **DMXDisplayClusterLightCard** (Runtime) – DMX-capable light card component built on `UDMXComponent`.

## 3. Important Types & APIs

- `UDMXDisplayClusterLightCardComponent` – DMX component that drives light card intensity/color from DMX fixture data.
- `FDMXDisplayClusterReplicator` – Tickable helper that listens for DMX input and pushes updates to light cards across the cluster.
- Module entry points `FDMXDisplayClusterModule` and `FDMXDisplayClusterLightCardModule` – Control startup and registration of the integration.

## 4. Typical usage patterns

- Enable DMX Engine, DMX Protocol, and this plugin in nDisplay-based projects.
- Add `UDMXDisplayClusterLightCardComponent` to light card actors that should react to DMX fixture patches.
- Configure DMX input ports (via DMX Protocol/Engine) and ensure the replicator is active so light card parameters mirror incoming DMX values across cluster nodes.
- Use DMX libraries/patches to map channels to the desired light card attributes for show control.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
