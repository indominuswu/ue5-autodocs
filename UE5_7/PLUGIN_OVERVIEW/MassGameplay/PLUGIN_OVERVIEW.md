# MassGameplay Plugin Overview

## 1. What this plugin does

- Implements large-scale, data-oriented agent simulation built on the Mass framework.
- Provides spawning, simulation phases, movement/LOD, EQS integration, smart objects, replication, and visualization for Mass entities.
- Includes editor/debug tooling for visualizing traits, processors, and agents.

## 2. Key Modules

- **MassCommon** (Runtime): Core Mass data/helpers shared across modules.
- **MassActors** (Runtime): Bridges Mass entities with actor components.
- **MassEQS** (Runtime): Environment Query System integration for Mass queries/processors.
- **MassSignals** (Runtime): Signal bus for Mass processors (`UMassSignalSubsystem`).
- **MassSpawner** (Runtime): Spawning/destruction pipeline for entities (`UMassSpawnerSubsystem`).
- **MassSmartObjects** (Runtime): Smart Object handlers and processors for Mass agents.
- **MassSimulation** (Runtime): Simulation phases and tick pipeline (`UMassSimulationSubsystem`).
- **MassLOD** (Runtime): Level-of-detail management for agents (`UMassLODSubsystem`).
- **MassMovement** (Runtime): Movement processors and fragments.
- **MassReplication** (Runtime): Network replication and viewer bubble management (`UMassReplicationSubsystem`).
- **MassRepresentation** (Runtime): Visualization/ISM handling for agents (`UMassRepresentationSubsystem`).
- **MassGameplayDebug** (Runtime): Debug overlays and tools (`UMassDebuggerSubsystem`).
- **MassGameplayEditor**, **MassMovementEditor** (Editor): Editor helpers, trait repository, and movement visualization.
- **MassGameplayExternalTraits** (Runtime): External/shared trait definitions.
- **MassGameplayTestSuite** (UncookedOnly): Test coverage for Mass gameplay features.

## 3. Important Types & APIs

### `UMassSimulationSubsystem`

- Role: Owns Mass processing phases, tick pipeline, and lifecycle (start/stop/pause) per world.
- Key behaviors: Manages phase delegates, rebuilds pipelines, integrates PIE begin/end, and tracks processing state.

### `UMassSignalSubsystem`

- Role: Lightweight signal/dispatch system for Mass processors.
- Key behaviors: `SignalEntity`, `SignalEntities`, delayed signals, and subscription helpers used by processors via `UMassSignalProcessorBase`.

### `UMassSpawnerSubsystem`

- Role: Spawns/destroys entities from `FMassEntityTemplate` definitions; caches initializer processors.
- Key functions: `SpawnEntities`, `DestroyEntities`, `GetMassEntityTemplate`.

### `UMassLODSubsystem`

- Role: Computes LOD state for agents and exposes commands to adjust LOD behavior (e.g., use player pawn vs camera).

### `UMassReplicationSubsystem`

- Role: Handles Mass entity replication, viewer bubbles, and mapping between network IDs and entities.
- Key behaviors: Synchronizes clients/viewers, registers bubble info classes, maps entities to replication IDs.

### `UMassRepresentationSubsystem`

- Role: Drives visualization (ISM/actor) for agents, hooked into simulation phases and agent component events.

### `UMassEQSSubsystem`

- Role: Integrates EQS generation/tests for Mass entities, used by MassEQS processors.

### Editor-facing classes

- `UMassDebuggerSubsystem`, `UMassDebugEntitySubsystem`, and `UMassActorEditorSubsystem` provide debug and editor utilities for inspecting agents/traits.

## 4. Typical usage patterns

- Enable `MassGameplay` to access the full Mass runtime stack; author fragments/tags and processors in game modules.
- Use `UMassSpawnerSubsystem` (Blueprint or C++) to spawn entities from templates; bind processors to phases via Mass configuration.
- Configure visualization/LOD/replication via Mass traits (e.g., representation traits) and rely on `UMassLODSubsystem` + `UMassRepresentationSubsystem` for scalability.
- Integrate with Smart Objects and EQS using the dedicated Mass modules; subscribe to signals to decouple processors.
- In the editor, use debug subsystems and visualization (MassGameplayDebug, MassMovementEditor) to inspect agents and pipelines during PIE.

## 5. Version-specific notes (UE 5.7)

- The plugin remains active (not marked deprecated). No additional UE 5.7-specific notes were found in source; functionality reflects the current Mass stack shipped with UE 5.7.
