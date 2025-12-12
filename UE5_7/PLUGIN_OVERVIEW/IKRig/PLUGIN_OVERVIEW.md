# IK Rig Plugin Overview

## 1. What this plugin does
- Provides IK Rig assets and runtime components for driving skeletal meshes with inverse-kinematics goals.
- Includes retargeting assets/workflows (IK Retargeter) to adapt animations between different skeletons.
- Ships with editor tooling (asset factories, anim instances) to author rigs and retarget profiles.
- Runtime component exposes Blueprint APIs to set IK goals per frame.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime IK rig component/Blueprint APIs plus editor asset factories/editors for rigs and retargeters.

## 3. Key Modules
- **IKRig** (Runtime)  
  - Runtime IK rig evaluation and Blueprint-facing APIs.  
  - Notable types: `UIKRigComponent`, `UIKRetargetSettings`.
- **IKRigDeveloper** (UncookedOnly)  
  - Developer helpers used during cooking/editor-only contexts.
- **IKRigEditor** (Editor)  
  - Asset factories/editors for IK Rig and IK Retargeter assets (`IKRigDefinitionFactory`, `IKRetargetFactory`, related asset type actions).

## 4. Important Types & APIs

### `UIKRigComponent`
- Role: Actor component implementing `IIKGoalCreatorInterface`; collects IK goals set from gameplay/Blueprint and feeds them to IK rig evaluation.
- Key functions: `SetIKRigGoalPositionAndRotation`, `SetIKRigGoalTransform`, `SetIKRigGoal`, `ClearAllGoals`.
- Goals are stored per name with separate position/rotation alphas and goal spaces.

### `UIKRetargetSettings`
- Role: Configuration object for retargeting settings used by IK Retargeter assets (bone/root motion adjustments, chain mappings).

### `UIKRetargetAnimInstance` / `UIKRigAnimInstance`
- Role: Editor-side anim instances used to preview retargeted animation and rig behavior inside the IK Rig / IK Retargeter editors.

## 5. Typical usage patterns
- Enable the IK Rig plugin (Animation category). Create IK Rig assets and IK Retargeter assets via the Content Browser (factories provided by the editor module).
- Add `UIKRigComponent` to an actor that owns a skeletal mesh; set IK goals each frame from Blueprint or C++ (e.g., hand/foot targets), then drive animation Blueprint nodes that consume those goals.
- For retargeting, open the IK Retargeter asset to map source/target chains; preview using the provided anim instances, then use the retargeted animations in Anim Blueprints or pipelines like UE’s Retarget Manager.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
