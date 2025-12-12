# Chaos Mover Plugin Overview

## 1. What this plugin does

- Provides Chaos-physics-based character movement using the Mover framework.
- Supplies character mover components, pathed movement helpers, and a world subsystem to feed physics input.
- Adds Blueprint-callable controls for launch/override events and exposes landing/jump delegates.

## 2. Editor/Runtime surfaces
- User-facing: Yes - exposes Chaos mover components and Blueprint controls for game authors to configure runtime character movement.

## 3. Key Modules

- **ChaosMover** (Runtime)  
  - Role: Core movement logic, components, and world subsystem integration for Chaos-driven mover simulations.
  - Notable types: `UChaosCharacterMoverComponent`, `UChaosMoverSubsystem`, `UChaosPathedMovementControllerComponent`, `UChaosPathedMovementDebugDrawComponent`.

## 4. Important Types & APIs

### `UChaosCharacterMoverComponent`
- Role: Chaos-backed character mover derived from `UCharacterMoverComponent`; drives movement input, floor detection, and mode transitions.
- Key properties/events: `OnLanded`, `OnJumped`, internal overrides for crouch, queued mode transitions, and launch settings.
- Key functions: `Launch`, `OverrideMovementSettings`, `CancelMovementSettingsOverrides`, floor hit accessors, and simulation event hooks.

### `UChaosMoverSubsystem`
- Role: `UWorldSubsystem` that registers mover backends, injects inputs per physics step, and hooks post-physics ticks.
- Behavior: Handles registration/unregistration of backend components and manages physics thread callbacks/async dispatch.

### `UChaosPathedMovementControllerComponent` and `UChaosPathedMovementDebugDrawComponent`
- Role: Components that control and visualize pathed Chaos mover motion; used to author/debug path-driven movement.

## 5. Typical usage patterns

- Enable the Chaos Mover plugin (runtime module only) for projects requiring Chaos-based character motion.
- Add `UChaosCharacterMoverComponent` to a character (Blueprint spawnable) to drive movement; bind `OnLanded`/`OnJumped` for gameplay reactions.
- Use `Launch` or movement override APIs to apply impulses/velocity effects and change mode settings at runtime.
- Pathed movement controllers/debug draw components can be added to author and visualize path-following behavior; the world subsystem registers mover backends automatically at play start.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
