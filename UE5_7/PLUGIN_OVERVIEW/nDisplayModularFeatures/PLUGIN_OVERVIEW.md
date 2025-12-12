# nDisplay Modular Features Plugin Overview

## 1. What this plugin does

- Provides modular feature interfaces that extend nDisplay workflows (e.g., light cards and stage actors).
- Allows external modules to register media initializers or actor extensions without modifying core nDisplay.
- Ships light-card extender interfaces plus editor wiring for integration in Configurator tooling.

## 2. Editor/Runtime surfaces

- User-facing: Yes - nDisplay extension points (`IDisplayClusterLightCardActorExtender`, media initializer modular features) that other plugins implement to add custom behavior to stage actors/light cards.

## 3. Key Modules

- **DisplayClusterLightCardExtender** (Runtime) – Runtime modular feature hooks for light card and stage actor extensions.
- **DisplayClusterModularFeaturesEditor** (Editor) – Editor integration for the modular feature providers (details, factories, Configurator support).

## 4. Important Types & APIs

### `IDisplayClusterLightCardActorExtender`

- Interface for supplying custom behavior or data to light card actors in nDisplay stages.

### `IDisplayClusterStageActor` / `FDisplayClusterWeakStageActorPtr`

- Interfaces and weak references used by extenders to interact with stage actors safely.

### `IDisplayClusterModularFeatureMediaInitializer`

- Hook for initializing media components on stage actors/light cards through the modular feature system.

### `FDisplayClusterPositionalParams` / `FDisplayClusterStageActorTemplate`

- Helper data structures used when spawning or modifying stage actor instances from extensible code.

## 5. Typical usage patterns

- Enable the plugin alongside nDisplay to allow other plugins to register `IModularFeature` implementations for light cards or stage actors.
- Implement `IDisplayClusterLightCardActorExtender` in a custom module to add data channels or behaviors to nDisplay light cards.
- Editor module surfaces the modular features in Configurator workflows so authored stages can use the extended capabilities.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; overview is based on the current plugin contents.

