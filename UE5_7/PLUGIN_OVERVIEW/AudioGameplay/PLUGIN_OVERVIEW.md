# AudioGameplay Plugin Overview

## 1. What this plugin does

- Core framework for gameplay-driven audio control (parameter routing, component pooling, tag-driven audio state).
- Adds reusable audio gameplay components and a world subsystem for tag caching.
- Includes optional automated tests for audio gameplay scenarios.

## 2. Key Modules

- **AudioGameplay** (Runtime)  
  - Role: Runtime components, subsystems, and utilities for gameplay-controlled audio.
- **AudioGameplayTests** (Editor)  
  - Role: Editor/automation tests for the runtime systems.

## 3. Important Types & APIs

### `UAudioGameplayComponent` (UActorComponent)

- Base component for gameplay audio behaviors; parent of parameter and volume components.

### `UAudioParameterComponent` (UAudioGameplayComponent)

- Role: Stores and dispatches audio parameters (via `ActorSoundParameterInterface`) to associated audio components.
- Key functions: `GetAllAudioComponents`, apply parameters to active audio components.

### `UAudioComponentGroup` (USceneComponent, IAudioParameterControllerInterface)

- Role: Pools and reuses `UAudioComponent` instances on an actor, applying shared parameters/modifiers.
- Key functions: `GetNextAvailableComponent`, `AddExternalComponent`, `ApplyParams`, `UpdateComponentParameters`.

### `UAudioComponentGroupExtension` (Interface)

- Role: Extension hook to update and react to group changes (update modifier, on component added/removed).

### `UAudioGameplayTagCacheSubsystem` (UWorldSubsystem)

- Role: Caches expensive-to-construct audio gameplay tags per world to avoid repeated generation.
- Key functions: Static `Get` to fetch the subsystem for a world.

### `USoundHandleSubsystem` (UAudioEngineSubsystem)

- Role: Engine-level subsystem managing sound handles for audio playback control.

## 4. Typical usage patterns

- Enable the plugin for gameplay projects needing pooled audio component management or parameter routing.
- Add `AudioParameterComponent` to actors to store and dispatch parameters to all child audio components.
- Use `AudioComponentGroup` to pool/reuse audio components and apply modifiers across a group.
- Leverage tag caching via `UAudioGameplayTagCacheSubsystem` when constructing tags dynamically at runtime.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
