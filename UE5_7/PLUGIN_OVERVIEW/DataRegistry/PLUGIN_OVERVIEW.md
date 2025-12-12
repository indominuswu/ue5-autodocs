# Data Registry Plugin Overview

## 1. What this plugin does

- Provides a generic system for querying structured data from multiple sources at runtime.
- Exposes Blueprint and C++ APIs for synchronous and asynchronous lookup of registry items.
- Includes optional editor support for customizing registry IDs and data sources.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Users configure registries in project settings and call `UDataRegistrySubsystem` Blueprint/C++ APIs to fetch data at runtime.

## 3. Key Modules

- **DataRegistry** (Runtime)  
  - Role: Core registry system, settings, and runtime lookup logic.
  - Notable types: `UDataRegistrySubsystem`, `UDataRegistry`, `FDataRegistryId`, `FDataRegistryLookup`, `UDataRegistrySettings`.
- **DataRegistryEditor** (UncookedOnly)  
  - Role: Editor customizations for registry IDs and settings.
  - Notable types: `FDataRegistryIdCustomization`.

## 4. Important Types & APIs

### `UDataRegistrySubsystem`
- Role: Engine subsystem offering Blueprint-accessible registry lookups.
- Key functions: `GetCachedItemBP`, `FindCachedItemBP`, `FindCachedItemFromLookupBP`, async acquire helpers.
- Key properties: Manages registry instances and caches for resolved lookups.

### `UDataRegistrySettings`
- Role: Project settings asset defining available registries and their data sources.
- Key properties: Registry definitions and source configurations.

### `FDataRegistryId` / `FDataRegistryLookup`
- Role: Identifiers used to reference registry items and resolved lookup handles.
- Key behavior: Support async resolve followed by cached retrieval.

## 5. Typical usage patterns

- Enable the plugin and configure registries in project settings via `UDataRegistrySettings`.
- Use Blueprint nodes from `UDataRegistrySubsystem` to fetch struct data by registry ID, optionally performing async acquire then cached lookup.
- Customize registry identifiers in the editor using the provided ID customization to reduce errors.

## 6. Version-specific notes (UE 5.7)

- No UE 5.7-specific notes surfaced; plugin remains optional and disabled by default in this branch.

