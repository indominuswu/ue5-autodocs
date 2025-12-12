# MassCrowd Plugin Overview

## 1. What this plugin does

- Spline based AI crowd system
- Derived from plugin metadata; see source for specifics.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Mass crowd runtime provides settings/subsystems (`UMassCrowdSettings`, `UMassCrowdSpawnerSubsystem`, `UMassCrowdRepresentationSubsystem`, zone graph annotations) that teams configure to simulate/render Mass-based crowds.

## 3. Key Modules

- **MassCrowd** (Runtime)

## 4. Important Types & APIs

- `UMassCrowdLaneDataRenderingComponent`
- `UMassCrowdRepresentationSubsystem`
- `UMassCrowdSettings`
- `UMassCrowdSpawnerSubsystem`
- `UMassCrowdSubsystem`
- `UZoneGraphAnnotationSubsystem`
- `UZoneGraphSubsystem`

## 5. Typical usage patterns

- Enable the plugin in the project/plugins manager; modules load accordingly.
- Use the classes above in game code or Blueprints where appropriate (traits, components, subsystems, or utility libraries based on naming).
- Editor modules (if present) add supporting tooling or debugging for the runtime modules.

## 6. Version-specific notes (UE 5.7)

- Marked experimental/beta in metadata.

