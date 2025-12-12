# MoverTests Plugin Overview

## 1. What this plugin does
- Provides sample/test content for the Mover system.
- Includes a custom layered move (`FTestCustomLayeredMove`) to validate launch-style impulses and movement mode forcing.
- Helps exercise Mover blackboard/tick integration without affecting production modules.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime test move class intended for validating Mover behavior.

## 3. Key Modules
- **MoverTests** (Runtime)
  - Role: Minimal test module defining custom layered move behavior for the Mover framework.

## 4. Important Types & APIs

### `FTestCustomLayeredMove`
- Role: Launch-style layered move for Mover testing; applies an impulse and can force a movement mode before execution.
- Key properties: `LaunchVelocity`, `ForceMovementMode`.
- Key functions: overrides `OnStart`, `GenerateMove`, `OnEnd`, `Clone`, `NetSerialize`, and `ToSimpleString` to integrate with layered move simulation and networking.

## 5. Typical usage patterns
- Enable the plugin and add the test move to Mover setups when validating layered move behavior.
- Use the move in automated or manual tests to confirm launch impulses, movement-mode forcing, and serialization.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
