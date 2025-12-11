# ArchVis Character Plugin Overview

## 1. What this plugin does
- Provides a first-person character tuned for architectural visualization walkthroughs.
- Includes a movement component optimized for smooth camera-style controls and input handling.
- Enabled by default for quick use in ArchViz projects.

## 2. Key Modules
- **ArchVisCharacter** (Runtime, Default)
  - Role: Character class and movement component implementation.

## 3. Important Types & APIs
- `AArchVisCharacter`
  - Role: Pawn class with input bindings for move/look, crouch, and configurable speeds.
  - Key properties: camera settings, acceleration/deceleration, rotation rate, movement speed parameters.
- `UArchVisCharMovementComponent`
  - Role: Custom movement component providing camera-style movement tuning and constraint handling.

## 4. Typical usage patterns
- Place `ArchVisCharacter` in ArchViz levels to provide immediate WASD/mouse navigation tuned for walkthroughs.
- Adjust movement settings on the character or movement component to match desired navigation feel (speed, acceleration, turning).
- Use as a starting point for non-combat first-person exploration experiences.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
