# ContextualAnimation Plugin Overview

## 1. What this plugin does

- Provides contextual animation scenes for coordinating multi-actor moves with shared entry/exit windows.
- Supplies runtime components to bind actors to contextual animation assets, manage warp targets, and replicate play state.
- Adds editor tooling to author contextual animation assets and preview scene bindings.
- Fits into the Animation stack as an experimental coordination layer on top of montages.

## 2. Key Modules

- **ContextualAnimation** (Runtime)  
  - Role: Runtime playback and replication of contextual animation scenes, including actor bindings and warp targets.
  - Notable types: `UContextualAnimSceneActorComponent`, `IContextualAnimActorInterface`, `UContextualAnimUtilities`.
- **ContextualAnimationEditor** (Editor)  
  - Role: Authoring, preview, and asset setup for contextual animation scenes inside the editor.

## 3. Important Types & APIs

### `UContextualAnimSceneActorComponent`
- Role: Component that binds an actor into a contextual animation scene, handles montage playback, replication, and warp target data.
- Key properties: Bindings data, warp targets, replicated montage info.
- Key functions: Montage start/stop notifications, warp target queries, replication helpers.

### `IContextualAnimActorInterface`
- Role: Interface for actors participating in contextual animations to expose attachment and playback hooks.
- Key functions: Accessors used by the component to drive role-specific behavior.

### `UContextualAnimUtilities`
- Role: Blueprint utility library for working with contextual animation assets, bindings, and warp targets.
- Key functions: Helpers to extract alignment transforms, binding data, and warp target definitions from assets.

## 4. Typical usage patterns

- Enable the plugin and create contextual animation assets in the editor; use the editor module to define roles, entry windows, and warp targets.
- Add a `UContextualAnimSceneActorComponent` to actors that should join a scene; bind them to a role and start playback via the component or utilities.
- Use blueprint utilities to query warp targets, alignment transforms, and to trigger scene starts or synchronized montage playback.
- Networked projects rely on the component’s replicated bindings/warp data to keep participants in sync.

## 5. Version-specific notes (UE 5.7)

- Marked as experimental in UE 5.7; no explicit 5.7-only APIs called out in source comments.
- No additional UE 5.7-specific notes found; this overview reflects the current plugin state in the UE 5.7 source tree.
