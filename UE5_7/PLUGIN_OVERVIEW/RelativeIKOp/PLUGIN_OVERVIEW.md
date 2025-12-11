# Relative IK Op Plugin Overview

## 1. What this plugin does
- Experimental retarget operator for setting IK goals relative to body motion.
- Supplies runtime ops for relative IK and body intersection plus editor utilities for authoring relative body animation data.
- Extends IKRig-based workflows with notifies and modifiers for relative body animation.

## 2. Key Modules
- **RelativeIKOp** (Runtime)
  - Role: Core retarget op definitions (`RelativeIKOp.h`, module bootstrap).
- **BodyIntersectIKOp** (Runtime)
  - Role: IK operator for handling body intersection scenarios (`BodyIntersectIKOp`).
- **RelativeBodyAnimInfo** (Runtime)
  - Role: Animation notifies and data helpers for relative body animation (`RelativeBodyAnimNotifies`).
- **RelativeBodyAnimUtils** (Editor)
  - Role: Editor-side modifiers/utilities (`RelativeBodyAnimModifier`, `RelativeBodyUtils`) for authoring relative body data.

## 3. Important Types & APIs
### `RelativeIKOp`
- Role: Defines the relative IK retarget operator used during animation retargeting.
- Key aspects: configuration of relative targets/goals for IK chains.

### `BodyIntersectIKOp`
- Role: Handles IK goal adjustments when limbs intersect with body geometry.

### `RelativeBodyAnimNotifies`
- Role: Animation notifies to mark relative body events used by the IK operators.

### `RelativeBodyAnimModifier` / `RelativeBodyUtils`
- Role: Editor utilities to bake or adjust relative body animation data.

## 4. Typical usage patterns
- Enable the plugin alongside IKRig.
- Author animations with `RelativeBodyAnimNotifies`; apply `RelativeBodyAnimModifier` to generate supporting data.
- Configure retarget setups to use `RelativeIKOp` (and optionally `BodyIntersectIKOp`) so IK goals adapt relative to body motion.
- Primarily used in retarget pipelines; not exposed as general gameplay components.

## 5. Version-specific notes (UE 5.7)
- Marked experimental in the `.uplugin`.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
