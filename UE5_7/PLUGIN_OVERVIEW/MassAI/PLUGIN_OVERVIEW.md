# MassAI Plugin Overview

## 1. What this plugin does

- AI-specific functionality extending MassGameplay
- Derived from plugin metadata; see source for specifics.

## 2. Key Modules

- **MassNavigation** (Runtime)
- **MassNavMeshNavigation** (Runtime)
- **MassZoneGraphNavigation** (Runtime)
- **MassNavigationEditor** (Editor)
- **MassAIBehavior** (Runtime)
- **MassAIBehaviorEditor** (Editor)
- **MassAIReplication** (Runtime)
- **MassAIDebug** (Runtime)
- **MassAITestSuite** (UncookedOnly)

## 3. Important Types & APIs

- `UCapsuleComponent`
- `UMassAgentSubsystem`
- `UMassBehaviorSettings`
- `UMassComponentHitSubsystem`
- `UMassDebuggerSubsystem`
- `UMassLookAtSettings`
- `UMassLookAtSubsystem`
- `UMassNavigationSubsystem`
- `UMassNavigationTestingComponent`
- `UMassSignalSubsystem`
- `UMassSimulationSubsystem`
- `UMassStateTreeSubsystem`
- `USmartObjectSubsystem`
- `UZoneGraphAnnotationSubsystem`
- `UZoneGraphSubsystem`
- `UZoneGraphTestingComponent`

## 4. Typical usage patterns

- Enable the plugin in the project/plugins manager; modules load accordingly.
- Use the classes above in game code or Blueprints where appropriate (traits, components, subsystems, or utility libraries based on naming).
- Editor modules (if present) add supporting tooling or debugging for the runtime modules.

## 5. Version-specific notes (UE 5.7)

- Marked experimental/beta in metadata.
