# CelestialVault Plugin Overview

## 1. What this plugin does

- Implements a DaySequence-based celestial vault for Earth using ephemeris calculations.
- Provides actor/components to drive directional light, sky, clouds, fog, and post process for time-of-day lighting.
- Includes editor tools for configuring vault parameters.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Place `ACelestialVaultDaySequenceActor` in levels and tune DaySequence-driven sky/lighting via the editor customizations on its components.

## 3. Key Modules

- **CelestialVault** (Runtime)  
  - Role: Runtime actor and components managing the celestial vault and sky rendering.
- **CelestialVaultEditor** (Editor)  
  - Role: Editor customization and tooling for configuring the celestial vault actor and assets.

## 4. Important Types & APIs

- `ACelestialVaultDaySequenceActor` (CelestialVault module)  
  - Role: DaySequence-based actor controlling sky elements; aggregates `UDirectionalLightComponent`, `USkyAtmosphereComponent`, `USkyLightComponent`, `UVolumetricCloudComponent`, `UExponentialHeightFogComponent`, `UPostProcessComponent`, and instanced mesh components for sun/moon visuals.

## 5. Typical usage patterns

- Place `ACelestialVaultDaySequenceActor` in a level to drive time-of-day sky lighting via DaySequence.
- Adjust lighting components (sun/sky/fog/clouds/post process) through the actor’s properties or editor customizations.
- Use DaySequence to animate celestial parameters over time for accurate ephemeris-driven lighting.

## 6. Version-specific notes (UE 5.7)

- Plugin marked experimental and disabled by default in this UE 5.7 tree.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

