# Motion Warping Plugin Overview

## 1. What this plugin does
- Provides a runtime system to modify root motion on the fly so animations align to dynamic targets (e.g., vault points, impacts).
- Exposes components and Blueprint utilities to define warp targets and extract root motion windows from animations.
- Supports attribute-driven root motion application for characters.

## 2. Key Modules
- **MotionWarping** (Runtime)  
  - Core motion warping runtime and utilities.  
  - Notable types: `UMotionWarpingComponent`, `UMotionWarpingUtilities`, `UAttributeBasedRootMotionComponent`, `UMotionWarpingFunctionLibrary`.

## 3. Important Types & APIs

### `UMotionWarpingComponent`
- Role: Actor component that manages warp targets and applies root-motion modifiers during animation playback.
- Key properties/APIs: multicast `OnPreUpdate`, flags for searching warp windows in montages, adapter creation (`CreateOwnerAdapter`), replication of warp targets.

### `UMotionWarpingUtilities`
- Role: Blueprint function library for extracting poses/root motion and warp windows from animations (`ExtractRootMotionFromAnimation`, `GetMotionWarpingWindowsFromAnimation`, `ExtractBoneTransformFromAnimationAtTime`, etc.).

### `UAttributeBasedRootMotionComponent`
- Role: Actor component applying root motion based on configurable attributes/modes; ticks pre-physics to apply deltas or velocities.
- Key property: `Mode` (`ApplyDelta` vs `ApplyVelocity`), `bEnableRootMotion`.

### `AttributeBasedRootMotionComponentPrePhysicsTickFunction`
- Role: Custom tick function wiring for the attribute-based component’s pre-physics updates.

## 4. Typical usage patterns
- Enable the plugin (Animation category). Add `UMotionWarpingComponent` to characters that use root-motion animations.
- Define warp targets (via animation notifies or gameplay code) and call utilities to extract warp windows; the component adjusts root motion to land on targets.
- Use `UAttributeBasedRootMotionComponent` when you need deterministic pre-physics application of root motion based on custom attributes.
- Blueprint nodes in `UMotionWarpingUtilities` help query animation windows and transforms when setting up motion-matching or vault/attack adjustments.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
