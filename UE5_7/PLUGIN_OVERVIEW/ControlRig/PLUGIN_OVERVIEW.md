# Control Rig Plugin Overview

## 1. What this plugin does

- Framework for animation driven by user controls.
- Derived from plugin metadata; see source for specifics.

## 2. Key Modules

- **ControlRig** (Runtime)
- **ControlRigDeveloper** (UncookedOnly)
- **ControlRigEditor** (Editor)

## 3. Important Types & APIs

- `UAnimationAuthoringSettings`
- `UAnimDetailsSettings`
- `UBakeToControlRigSettings`
- `UControlRigComponent`
- `UControlRigEditModeSettings`
- `UControlRigEditorSettings`
- `UControlRigPoseProjectSettings`
- `UControlRigSettings`
- `UControlRigSkeletalMeshComponent`
- `UControlRigSnapSettings`
- `UCreateControlPoseAssetRigSettings`
- `ULevelEditorViewportSettings`
- `ULoadAnimToControlRigSettings`
- `USceneComponent`
- `USelectionSetsSettings`
- `USkeletalMeshComponent`
- `UStaticMeshComponent`

## 4. Typical usage patterns

- Enable the plugin in the project/plugins manager; modules load accordingly.
- Use the classes above in game code or Blueprints where appropriate (traits, components, subsystems, or utility libraries based on naming).
- Editor modules (if present) add supporting tooling or debugging for the runtime modules.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific or experimental notes found.
