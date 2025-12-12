# SpatialReadiness Plugin Overview

## 1. What this plugin does
- Experimental system to mark and query “ready/unready” spatial volumes in a world.
- Allows gameplay code to track readiness of volumes and receive updates when readiness changes.
- Integrates with Chaos physics data (ChaosUserDataPT dependency) for simulation callbacks.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Gameplay subsystem (`USpatialReadiness`/volume component) that developers use to register readiness volumes and query/subscribe to readiness state.

## 3. Key Modules
- **SpatialReadiness** (Runtime)
  - Role: Manages readiness volumes via a world subsystem and optional volume components.
  - Notable types: `USpatialReadiness`, `USpatialReadinessVolumeComponent`, `FSpatialReadinessVolume`, `FSpatialReadinessAPI`.

## 4. Important Types & APIs
- `USpatialReadiness` (UWorldSubsystem)
  - Role: Core manager providing APIs to add/query readiness volumes and broadcast changes.
  - Key functions: `AddReadinessVolume`, `QueryReadiness`, `GetNumUnreadyVolumes`, `OnUnreadyVolumeChangedDelegate_AddUObject`, `OnUnreadyVolumeChangedDelegate_Remove`, `StaticShouldCreateSubsystem`.
- `USpatialReadinessVolumeComponent` (UActorComponent)
  - Role: Component representation of readiness volumes; interacts with the subsystem for lifecycle.
- `FSpatialReadinessAPI` / `FSpatialReadinessSimCallback`
  - Role: Internal helpers for physics-side callbacks and volume bookkeeping.

## 5. Typical usage patterns
- Enable the experimental plugin; ensure Chaos physics is available (ChaosUserDataPT dependency).
- In code, access `USpatialReadiness` from the world to register volumes (via `AddReadinessVolume` or volume components).
- Query readiness for bounding boxes to gate gameplay (e.g., streaming, safety checks) and subscribe to the unready-volume delegate for notifications.
- Use debug drawing hooks (enabled in non-shipping builds) to visualize readiness volumes during development.

## 6. Version-specific notes (UE 5.7)
- Marked experimental in the `.uplugin`; no additional UE 5.7-specific notes found.

