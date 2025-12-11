# AsyncMessageSystem Plugin Overview

## 1. What this plugin does

- Experimental framework for an async gameplay message bus scoped per world.
- Provides Blueprint nodes to post and listen for messages without tight coupling.
- Supplies a world subsystem and optional binding component to manage message lifetimes.
- Configurable developer settings for message handling.

## 2. Key Modules

- **AsyncMessageSystem** (Runtime)  
  - Role: Core async message routing, Blueprint helpers, and world subsystem.

## 3. Important Types & APIs

### `UAsyncMessageWorldSubsystem`

- Role: World subsystem that owns the shared async message system; exposes helper accessors to fetch per-world message system instances.
- Key functions: `GetSharedMessageSystem`, `Initialize`/`ShutdownMessageSystem`, `ShouldCreateSubsystem`.

### `UAsyncMessageBindingComponent`

- Role: Actor component that binds gameplay actors to the async message system and manages registration/unregistration.
- Key properties: Arrays of binding info for message endpoints; integrates with actor lifecycle.

### `UAsyncMessageSystemBlueprintLibrary`

- Role: Blueprint function library for posting messages and querying the async message system from Blueprints.
- Key functions: Helpers to send messages and interact with the subsystem in a Blueprint-friendly manner.

### `UAsyncAction_ListenForAsyncMessage`

- Role: Blueprint latent action to asynchronously listen for specific messages on a world’s message system.
- Key functions: Starts listening given message descriptors; automatically unregisters on completion or cancel.

### `UAsyncMessageDeveloperSettings`

- Role: Project-level developer settings to configure async message system defaults (e.g., whether to reuse shared systems, debug flags).

## 4. Typical usage patterns

- Enable the plugin (experimental) in the project.
- Add `UAsyncMessageBindingComponent` to actors that should register message handlers or endpoints.
- In Blueprints, use `Async Action Listen For Async Message` to subscribe to a message key; handle the completion pin when a message is received.
- Use `AsyncMessageSystemBlueprintLibrary` helpers to publish messages to the current world’s `UAsyncMessageWorldSubsystem`.

## 5. Version-specific notes (UE 5.7)

- Marked as experimental in the `.uplugin`.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
