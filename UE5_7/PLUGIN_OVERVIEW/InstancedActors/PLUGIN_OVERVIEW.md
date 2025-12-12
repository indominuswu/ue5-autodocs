# InstancedActors Plugin Overview

## 1. What this plugin does

- Experimental Mass-based system for managing large numbers of actor instances via instanced static meshes and data registries.
- Provides runtime subsystems for spawning, representing, and modifying instanced actors on server and client.
- Includes editor tools for converting actors to instanced actors and previewing instance data.
- Ships with an uncooked test suite module for validation.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime Mass subsystems/components for instanced actors plus editor conversion/inspection tools.

## 3. Key Modules

- **InstancedActors** (Runtime) — Core Mass integration, subsystems, components, and data structures for instanced actor management.
- **InstancedActorsEditor** (Editor) — Editor actions for converting actors to instanced actors and inspecting instance data.
- **InstancedActorsTestSuite** (UncookedOnly) — Test scaffolding and validation.
- Plugin dependencies: `MassGameplay`, `DataRegistry`, `GameFeatures`.

## 4. Important Types & APIs

### `UInstancedActorsSubsystem` (TickableWorldSubsystem)

- Role: Central manager for instanced actor grids, exemplar actors, modifier volumes, and instance lifecycle.
- Key functions: `Get`/`GetChecked`, `InstanceActor`, `RemoveActorInstance`, modifier volume registration, and per-tick updates.

### `UInstancedActorsComponent` (UActorComponent)

- Role: Component added to instanced actor classes to bind them to Mass entities, manage fragments, and handle per-instance data (handles, mass fragments, persistence).
- Key hooks: fragment add/remove helpers, serialization for instance persistence, and links to `UMassRepresentationSubsystem`.

### `UInstancedActorsModifierVolumeComponent` / `URemoveInstancesModifierVolumeComponent` (UPrimitiveComponent)

- Role: Volumes that apply modifiers (culling, removal, or custom effects) to instances within bounds; registered with the subsystem.
- Key properties: modifier lists, registration handles; removal variant comes preconfigured to remove instances.

### `UClientInstancedActorsSpawnerSubsystem` / `UServerInstancedActorsSpawnerSubsystem` (UMassActorSpawnerSubsystem)

- Role: Mass spawner subclasses for client/server; coordinate actor spawning and initialization for instanced actors.
- Server variant offers `OnInstancedActorComponentInitialize` to extend actor setup before `BeginPlay`.

### `UInstancedActorsProjectSettings` (UDeveloperSettings)

- Role: Project-level configuration pointing to spawner subsystem classes, subsystem class overrides, and data registry assets for named/class settings.
- Provides accessors used during subsystem initialization.

### `UInstancedActorsRepresentationSubsystem` (UMassRepresentationSubsystem)

- Role: Representation binding that links instance data to ISM components and Mass visualization descriptors.

## 5. Typical usage patterns

- Configure `InstancedActorsProjectSettings` with desired spawner/subsystem classes and data registry assets for settings.
- Convert actors to instanced actors via the editor module actions; exemplar actors are created and managed by `UInstancedActorsSubsystem`.
- Add `UInstancedActorsComponent` to actor classes to participate in instancing; use modifier volumes to cull or adjust instance behavior.
- Mass representation is used for rendering; ensure required Mass plugins are enabled (dependencies already declared).

## 6. Version-specific notes (UE 5.7)

- Marked experimental in the descriptor; no additional UE 5.7-specific flags beyond the experimental designation were identified.
