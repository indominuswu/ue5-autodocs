# Mover Plugin Overview

## 1. What this plugin does

- Provides a rollback-friendly movement framework for actors, separating movement logic from engine physics backends.
- Supplies a configurable `UMoverComponent` with default movement sets (character, nav, pathed physics) and layered move/mode architecture.
- Integrates with network prediction, network physics, and standalone/physics backends through liaison components.
- Includes Chaos Visual Debugger (CVD) data hooks and developer settings for tuning/debugging.
- Experimental and off by default.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime movement components/backends with optional editor helpers and CVD visualization hooks.

## 3. Key Modules

- **Mover** (Runtime) — core movement component, movement modes, layered move system, network/physics backends, and developer settings.
- **MoverCVDData** (Runtime) — runtime data structures for Chaos Visual Debugger integration.
- **MoverEditor** (UncookedOnly) — editor-side helpers for authoring Mover assets and settings.
- **MoverCVDEditor** (UncookedOnly) — Chaos Visual Debugger extensions for visualizing Mover simulation data.

## 4. Important Types & APIs

- `UMoverComponent` — central actor component implementing movement simulation and rollback support; owns moves, modes, and backend coordination.
- Default movement set components:
  - `UCharacterMoverComponent` / `UPhysicsCharacterMoverComponent` — character-oriented movement built on the Mover pipeline.
  - `UNavMoverComponent` — nav-walking support implementing `INavMovementInterface`.
  - `UPathedPhysicsMoverComponent` — pathed physics movement with debug draw support.
- Backend liaison components:
  - `UMoverNetworkPredictionLiaisonComponent` (`UNetworkPredictionComponent`) — connects Mover to the Network Prediction system.
  - `UMoverNetworkPhysicsLiaisonComponent` / `UMoverNetworkPhysicsLiaisonComponentBase` — network physics bridge for deterministic simulation.
  - `UMoverStandaloneLiaisonComponent` — standalone (non-networked) backend adapter.
  - `UMoverPathedPhysicsLiaisonComponent` — liaison for pathed physics mover.
- Supporting types:
  - `UMoverDebugComponent` — debug visualization and controls.
  - Movement settings objects such as `UCommonLegacyMovementSettings` and `UStanceSettings` implementing `IMovementSettingsInterface`.
  - Layered move/modifier types (`FLayeredMoveFinishVelocitySettings`, `MovementModifiers`, `LayeredMoves`, `MovementModeTransition`) defining how moves blend and resolve.
  - `UMoverDeveloperSettings` — developer settings backed by CVars for tuning.
  - CVD helpers: `UMoverCVDSimDataComponent`, `UMoverPoseSearchTrajectoryPredictor`, `UPathedPhysicsDebugDrawComponent`.

## 5. Typical usage patterns

- Enable the plugin and attach `UMoverComponent` (or a derived component such as `UCharacterMoverComponent`/`UNavMoverComponent`) to actors that need rollback-capable movement.
- Choose a backend liaison component (standalone, network prediction, or network physics) appropriate to your project and register it with the mover component.
- Configure movement modes and layered moves in code/data to model walking, flying, falling, pathed motion, or custom behaviors; use movement modifier structs to tweak stance and acceleration.
- Use the debug component and CVD integration to inspect simulations, network traces, and pathed physics data during iteration.

## 6. Version-specific notes (UE 5.7)

- Plugin is experimental in 5.7; no additional version-specific flags beyond the current module layout.
