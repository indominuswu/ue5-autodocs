# DMX Fixtures Plugin Overview

## 1. What this plugin does

- Supplies example DMX fixture actors and components for quickly driving light-style behaviors from DMX data.
- Provides reusable component types for single/double channels and color mixing.
- Serves as sample content to pair with DMX Engine libraries and controllers.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Runtime DMX fixture actors/components that users place and map to DMX patches to drive lights/props in virtual production or live control setups.

## 3. Key Modules

- **DMXFixtures** (Runtime) - Fixture actor implementations and supporting components/interpolation utilities.

## 4. Important Types & APIs

- `ADMXFixtureActorBase` / `ADMXFixtureActor` / `ADMXFixtureActorMatrix` - Example actors that interpret DMX attributes and drive transforms/intensity/color (including matrix fixtures).
- `UDMXFixtureComponent` and specializations (`UDMXFixtureComponentSingle`, `UDMXFixtureComponentDouble`, `UDMXFixtureComponentColor`) - Component-level interpretation of DMX channels.
- `FDMXInterpolation` - Utility for smoothing DMX-driven values over time.

## 5. Typical usage patterns

- Enable DMX Engine and DMX Fixtures; place `ADMXFixtureActor` (or the matrix variant) in a level and assign a `UDMXEntityFixturePatch` from a DMX Library.
- Configure fixture components to map DMX attributes (intensity, color, pan/tilt) to actor properties; use interpolation to avoid stepping.
- Use these actors as starting points or references when building custom DMX-driven fixtures for virtual production or live events.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

