# Replication Graph Plugin Overview

## 1. What this plugin does
- Provides a graph-based replication driver optimized for large actor counts and many connections.
- Maintains persistent actor lists in graph nodes (spatial, always-relevant, per-connection) instead of per-frame building.
- Includes a basic implementation and debug tools to aid integration.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Developer-facing replication framework (`UReplicationGraph`/`UBasicReplicationGraph`, debug actor) selected via config to customize replication behavior for large games.

## 3. Key Modules
- **ReplicationGraph** (Runtime)  
  - Core replication graph framework, node types, debug actor, and a basic default graph implementation.

## 4. Important Types & APIs
### `UReplicationGraph`
- Role: Base class for custom replication graphs; override `InitGlobalActorClassSettings`, `InitGlobalGraphNodes`, `InitConnectionGraphNodes`, and routing methods.
- Provides `ServerReplicateActors` and node traversal APIs.

### `UBasicReplicationGraph`
- Role: Example/configurable graph that supports NetCullDistanceSquared, `bAlwaysRelevant`, and owner-only replication.
- Nodes: `UReplicationGraphNode_GridSpatialization2D`, `UReplicationGraphNode_ActorList`, and per-connection `UReplicationGraphNode_AlwaysRelevant_ForConnection`.

### Debugging types
- `AReplicationGraphDebugActor`, various debug commands/events declared in `ReplicationGraph.h` for inspecting graph state.

## 5. Typical usage patterns
- Enable the plugin and set `[/Script/OnlineSubsystemUtils.IpNetDriver] ReplicationDriverClassName="/Script/ReplicationGraph.BasicReplicationGraph"` (or your subclass) in config.
- Derive from `UReplicationGraph` to build a custom hierarchy of nodes for your game’s replication strategy; override routing to place actors in nodes.
- Use the debug actor/commands to visualize replication state and performance during development.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

