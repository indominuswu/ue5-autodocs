# Global Configuration Data Plugin Overview

## 1. What this plugin does

- Introduces a system for querying configuration values from multiple sources (config files, console commands) at runtime.
- Exposes a Blueprint library for retrieving typed configuration data keyed by name.
- Provides router interfaces to plug in different configuration data providers.

## 2. Key Modules

- **GlobalConfigurationData** (Runtime)  
  - Role: Blueprint-facing API for fetching configuration data.  
  - Notable types: `UGlobalConfigurationDataBlueprintLibrary`.

- **GlobalConfigurationDataCore** (Runtime)  
  - Role: Core router interfaces and implementations for data sources.  
  - Notable types: `FGlobalConfigurationData`, `FGlobalConfigurationRouter`, `FGlobalConfigurationConfigRouter`, `FGlobalConfigurationConsoleCommandRouter`.

## 3. Important Types & APIs

### `UGlobalConfigurationDataBlueprintLibrary`

- Role: Blueprint-callable accessors to get configuration values routed through the registered providers.
- Key functions: Retrieve values by key/name using the configured router stack.

### `FGlobalConfigurationRouter` and derived routers

- Role: Abstract interface for resolving configuration requests; implementations include config-file router and console-command router.
- Key properties: Source identifiers, priority ordering, optional caching.

### `FGlobalConfigurationData`

- Role: Holds the consolidated configuration data exposed via routers.

## 4. Typical usage patterns

- Enable the plugin, register desired routers (config and/or console) at startup, and call the Blueprint library to query configuration values from gameplay code or blueprints.
- Extend `FGlobalConfigurationRouter` to add custom data sources, then plug them into the system to resolve configuration keys.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
