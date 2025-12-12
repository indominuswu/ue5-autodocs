# Gameplay Cameras Plugin Overview

## 1. What this plugin does
- Implements a modular, data-driven gameplay camera system with reusable camera assets and rigs.
- Provides runtime components to evaluate camera assets, manage parameter overrides, and drive view rotation/IK aiming.
- Includes extensive editor tooling for creating camera assets, rigs, shakes, and Sequencer tracks.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime camera components/rigs and editor asset factories/Sequencer track editors for gameplay cameras.

## 3. Key Modules
- **GameplayCameras** (Runtime)  
  - Core runtime camera evaluation and components.  
  - Notable types: `UGameplayCameraComponent`, `UGameplayCameraComponentBase`, `UGameplayCameraRigComponent`, `UGameplayCameraSystemComponent`, `UGameplayCameraParameterSetterComponent`, `UGameplayControlRotationComponent`, `UBlueprintCameraDirector`, `UGameplayCamerasSettings`, camera nodes/assets utilities, `PostProcessSettingsCollection`.
- **GameplayCamerasUncookedOnly** (UncookedOnly)  
  - Editor-only glue used during uncooked sessions (graph pins, schemas).
- **GameplayCamerasEditor** (Editor)  
  - Asset factories, component visualizers, Sequencer track editors, and editor settings.  
  - Notable types: `GameplayCameraActorFactory`, `GameplayCameraRigActorFactory`, `CameraAssetFactory`, `CameraRigAssetFactory`, `CameraRigProxyAssetFactory`, `CameraShakeAssetFactory`, `CameraVariableCollectionFactory`, `GameplayCamerasEditorSettings`, graph panel pin factories, editor toolkits (`AssetEditorMode`, `BlueprintCameraDirectorAssetEditorMode`), `GameplayCameraComponentTrackEditor`.

## 4. Important Types & APIs

### `UGameplayCameraComponent` / `UGameplayCameraSystemComponent`
- Role: Components that run camera assets inside their own evaluation contexts; system component aggregates rigs/components on actors and manages view contributions.
- Key APIs: assign `FCameraAssetReference`, update evaluation context, blend parameter overrides; system component coordinates per-actor camera stacks.

### `UGameplayCameraRigComponent`
- Role: Drives camera rigs attached to actors, enabling modular camera setups; works with rig assets and parameter setters.

### `UGameplayCameraParameterSetterComponent`
- Role: Applies parameter overrides (e.g., post-process, FOV) to active camera graphs at runtime.

### `UGameplayControlRotationComponent`
- Role: Manages player control rotation integration with gameplay cameras (view rotation modes, IK aiming support).

### `UBlueprintCameraDirector`
- Role: Blueprint director asset for camera logic; provides Blueprint-accessible evaluation data/poses.

### `UGameplayCamerasSettings`
- Role: Developer settings (auto-build in PIE, default view rotation mode, IK aiming tolerances/iterations).

### Editor factories and toolkits
- Role: Create camera assets/rigs/shakes/variable collections; provide graph pin factories and Sequencer track editors for authoring and preview.

## 5. Typical usage patterns
- Enabled by default. Create camera assets/rigs via the provided factories, then place `UGameplayCameraComponent` or `UGameplayCameraRigComponent` on actors to run them.
- Configure global defaults in `UGameplayCamerasSettings` (auto-build, view rotation, IK aiming tolerances).
- Use `UGameplayCameraParameterSetterComponent` to apply overrides per actor or gameplay state; combine multiple rigs through `UGameplayCameraSystemComponent`.
- In the editor, use the camera-specific asset editors, graph pin factories, and Sequencer track editors to author and preview camera behavior; `GameplayCameraComponentTrackEditor` integrates with Sequencer.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
