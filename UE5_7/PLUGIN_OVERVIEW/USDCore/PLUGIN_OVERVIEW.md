# USD Core Plugin Overview

## 1. What this plugin does

- Provides the underlying USD SDK bindings, wrapper classes, and conversion utilities used by Unreal for Universal Scene Description (USD) workflows.
- Supplies UObject-based helpers for caching USD assets, managing metadata, and exposing USD settings to projects.
- Acts as the runtime foundation for higher-level USD tools such as USD Importer/Stage Editor.

## 2. Key Modules

- **UnrealUSDWrapper** (Runtime)  
  - Role: Low-level bridge to the Pixar USD SDK (schema bindings, stage wrappers).
- **USDUtilities** (Runtime)  
  - Role: Conversion utilities for translating USD prims, meshes, lights, and animation into Unreal assets and components.
- **USDClasses** (Runtime)  
  - Role: UObject layer exposing USD-specific asset caches, metadata helpers, draw-mode rendering components, and project settings.

## 3. Important Types & APIs

### `UUsdProjectSettings`

- Role: Developer settings for global USD behavior (plugin search paths, default resolver search paths, additional material purposes, extra schema names, logging control).
- Key properties: `AdditionalPluginDirectories`, `DefaultResolverSearchPath`, `AdditionalMaterialPurposes`, `AdditionalCustomSchemaNames`, logging level toggles and edit-in-instance prompts.

### `UUsdDrawModeComponent`

- Role: Primitive component used to render USD “draw mode” stand-ins (e.g., bounds boxes) inside Unreal.
- Key properties: Overrides for visibility and collision; integrates with USD draw mode materials.

### Asset cache and metadata helpers

- `UUsdAssetCache3` / `UUsdAssetCache2` / `UUsdAssetCache`: UObject caches for USD-authored assets generated during conversion/import, optionally blueprint-accessible.
- `UUsdAssetUserData`, `UUsdAssetImportData`, `FUsdStageOptions`, `FUsdReferenceOptions`, `FUsdMetadata` utility types to persist USD metadata and import options on assets.

## 4. Typical usage patterns

- Enable USD Core (usually indirectly via USD Importer) to allow USD stages to be opened and converted.
- Configure project-wide USD behavior in Project Settings → USDCore (paths for USD plugins, resolver search path, material purposes, schema lists, logging verbosity).
- Use asset caches (`UUsdAssetCache3`) when importing or live-updating USD scenes so generated meshes/materials can be reused across prims.
- Attach `UUsdDrawModeComponent` when rendering USD prim stand-ins that rely on USD draw modes instead of fully converted assets.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
