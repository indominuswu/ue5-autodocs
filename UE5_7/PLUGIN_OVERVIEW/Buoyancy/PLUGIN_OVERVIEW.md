# Buoyancy Plugin Overview

## 1. What this plugin does

- Experimental runtime tools for adding buoyant behavior to objects interacting with Water plugin water bodies.
- Provides buoyancy computation helpers, runtime settings, and spline-based water surface data structures.
- Designed to be paired with the Water plugin’s waves/splines rather than general physics.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime exposes `UBuoyancySubsystem`, `IBuoyancyEventInterface`, and `UBuoyancyRuntimeSettings` for developers to add buoyant actors with Water plugin data.

## 3. Key Modules

- **Buoyancy** (Runtime)  
  - Role: Core buoyancy algorithms, runtime settings, subsystem, and supporting data types.

## 4. Important Types & APIs

- `UBuoyancySubsystem`: Central subsystem managing buoyancy data and interactions with water splines.
- `UBuoyancyRuntimeSettings`: Project settings controlling buoyancy simulation defaults.
- Data/utility classes: `FBuoyancyParticleData`, `FBuoyancyWaterSplineData`, `FBuoyancyWaterSplineKeyCacheGrid`, `FBuoyancyEventFlags`, `IBuoyancyEventInterface`.
- Algorithm helpers: `FBuoyancyAlgorithms`, `FBuoyancyStats`, `FBuoyancyMacros`.

## 5. Typical usage patterns

- Enable the plugin alongside the Water plugin when you need buoyant actors.
- Use `UBuoyancySubsystem` to query or register buoyant objects against water spline data; implement `IBuoyancyEventInterface` on actors/components that should respond to buoyancy events.
- Adjust defaults in `UBuoyancyRuntimeSettings` (e.g., forces, sampling parameters) to tune simulation.

## 6. Version-specific notes (UE 5.7)

- Marked experimental and disabled by default.
- No explicit UE 5.7-specific notes found.

