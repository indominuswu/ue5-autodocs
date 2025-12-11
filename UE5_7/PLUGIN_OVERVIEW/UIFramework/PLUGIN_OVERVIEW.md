# UIFramework Plugin Overview

## 1. What this plugin does

- Experimental framework for driving UMG-like UI from the server, replicating a widget tree to clients.
- Provides game-layer slotting, input mode control, and asset fallback handling for replicated UI.
- Integrates with MVVM/LocalizableMessage dependencies for data binding and text delivery.

## 2. Key Modules

- **UIFramework** (Runtime)  
  - Role: Core runtime that owns the replicated widget tree, game-layer slots, and input handoff for UI rendered on clients.  
  - Notable types: `UUIFrameworkPlayerComponent`, `UUIFrameworkLocalSettings`.

## 3. Important Types & APIs

### `UUIFrameworkPlayerComponent`

- Role: Blueprint-spawnable `UActorComponent` that owns the replicated UI widget tree and game-layer slots for a player. Implements `IUIFrameworkWidgetTreeOwner`.
- Key properties/structures:
  - `FUIFrameworkGameLayerSlot` entries (Z-order, input mode, layer type) replicated via `FUIFrameworkGameLayerSlotList`.
  - Connection points for adding/removing replicated widgets and handling pending replication callbacks (`FOnPendingReplicationProcessed`).
- Usage: Attach to the controlling actor (e.g., player controller/pawn) to create and replicate UIFramework widgets; manage game-layer slots and input routing per player.

### `UUIFrameworkLocalSettings`

- Role: Developer settings storing soft references to error/loading placeholder assets used by the framework.
- Key properties: `ErrorResource`, `LoadingResource`; `LoadResources()` resolves them at runtime. Does not load on server.

## 4. Typical usage patterns

- Enable the plugin, then attach `UUIFrameworkPlayerComponent` to the player controller or pawn that should own the replicated UI tree.
- Build widgets using UIFramework widget types, assign them to `FUIFrameworkGameLayerSlot` entries to control Z-order and whether input is routed to UI or game.
- Configure placeholders in Project Settings → UI Framework Local Settings so missing assets show a defined fallback instead of errors.
- Expect server authority to own widget creation/update; clients receive replicated widget data and render via UMG.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
