# Mover Examples Plugin Overview

## 1. What this plugin does

- Supplies sample code, test maps, and helper classes demonstrating the Mover framework.
- Provides example characters and movement bases showing how to wire Mover components into gameplay.
- Not intended for shipping; disabled by default to keep sample content separate.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Sample gameplay classes/maps for Mover to reference in editor or runtime.

## 3. Key Modules

- **MoverExamples** (Runtime) — example gameplay classes built on top of the Mover plugin.

## 4. Important Types & APIs

- `AMoverExamplesCharacter` — sample character class using `UCharacterMoverComponent`/`UNavMoverComponent` with input setup.
- `FFollowSplineMode` (in `FollowSplineMode.h`) — example movement mode that follows a spline via `USplineComponent`.
- Additional sample movement bases and utility code illustrating how to consume mover outputs.

## 5. Typical usage patterns

- Enable alongside the core Mover plugin to review or run the provided sample maps.
- Inspect `AMoverExamplesCharacter` and movement mode implementations as references when building custom mover-based characters.
- Use as a learning/testbed; avoid depending on these classes in production gameplay.

## 6. Version-specific notes (UE 5.7)

- Marked sample/non-shipping; no additional UE 5.7-specific behaviors noted.
