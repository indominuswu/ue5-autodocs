# Modular Gameplay Plugin Overview

## 1. What this plugin does

- Supplies base classes and subsystems for building modular gameplay features that attach components to framework actors.
- Centralizes lifecycle management for modular components across controllers, pawns, player states, and game states.
- Designed to help feature plugins add gameplay pieces without subclassing core gameplay classes.
- Disabled by default so projects can opt into the modular pattern.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Teams derive from `UGameFrameworkComponent`/`UControllerComponent`/`UPawnComponent` and register them via `UGameFrameworkComponentManager` to add modular features to framework actors without subclassing.

## 3. Key Modules

- **ModularGameplay** (Runtime) — core runtime support for modular components and the component manager.

## 4. Important Types & APIs

- `UGameFrameworkComponent` — base actor component class used for modular gameplay pieces.
- `UGameFrameworkComponentManager` (`UGameInstanceSubsystem`) — registers component requests, attaches components at runtime, and tracks add/remove flags/results.
- `UControllerComponent`, `UPawnComponent`, `UPlayerStateComponent`, `UGameStateComponent` — concrete component bases for common gameplay framework classes.
- Helper enums/structs (`EGameFrameworkAddComponentFlags`, `EGameFrameworkAddComponentResult`, `FComponentRequestHandle`) — describe component registration and lifecycle results.
- `IGameFrameworkInitStateInterface` — governs initialization state for modular components.

## 5. Typical usage patterns

- Enable the plugin and derive modular features from `UGameFrameworkComponent` subclasses instead of subclassing core actors.
- Register components with `UGameFrameworkComponentManager` so they are attached when matching actors (controller, pawn, player state, game state) are created.
- Use the init state interface and add-component flags to coordinate initialization order and dependencies between modular pieces.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes; code reflects the current modular framework shipped with 5.7.

