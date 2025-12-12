# UAF Warping Plugin Overview

## 1. What this plugin does

- Adds animation/pose warping traits for UAF/AnimNext graphs.
- Supplies steering and strafe-warping behaviors plus test utilities for warping workflows.
- Disabled by default.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Provides warping traits (`FStrafeWarpingTrait`, `FSteeringTrait`, test trait) that AnimNext authors add to graphs to adjust movement/pose behavior.

## 3. Key Modules

- **UAFWarping** (Runtime)
  - Role: Runtime warping traits and supporting logic.

## 4. Important Types & APIs

### `FStrafeWarpingTrait`

- Role: Trait implementing strafing warps to adjust motion to targets or input.

### `FSteeringTrait`

- Role: Trait providing steering adjustments within AnimNext graphs.

### `FWarpTestTrait`

- Role: Test trait to exercise warping behavior in sample graphs.

## 5. Typical usage patterns

- Add warping traits to AnimNext graphs to correct or adapt movement (e.g., strafing to match locomotion targets).
- Use the test trait when validating new warping configurations.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

