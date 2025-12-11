# RigMapper Op Plugin Overview

## 1. What this plugin does
- Experimental retarget operator that uses RigMapper definitions to remap curves/poses during retargeting.
- Extends IKRig workflows with a RigMapper-backed retarget op.

## 2. Key Modules
- **RigMapperOp** (Runtime)
  - Role: Implements the retarget operator tying RigMapper definitions into retarget chains (`RigMapperOp.h`, module bootstrap).
  - Depends on IKRig and RigMapper.

## 3. Important Types & APIs
### `RigMapperOp`
- Role: Retarget operator applying RigMapper definitions while retargeting animations.
- Key properties: reference to a mapper definition, options for curve remapping.

### `FRigMapperOpModule`
- Role: Module setup and registration for the operator.

## 4. Typical usage patterns
- Enable RigMapper Op along with IKRig and RigMapper.
- Configure retarget setups to include the RigMapper operator and point it to a RigMapper definition asset.
- Use when retargeting animations that need curve/pose remapping beyond standard IK goals.

## 5. Version-specific notes (UE 5.7)
- Marked experimental in the `.uplugin`.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
