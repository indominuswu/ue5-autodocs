# USD Importer Plugin Overview

## 1. What this plugin does

- Adds end-to-end support for importing, opening, and editing USD stages inside Unreal Engine.
- Provides runtime stage actor support plus extensive editor tooling for stage browsing, conversion, export, and USD schema handling.
- Includes translators for meshes, lights, animation, groom, geometry cache, and material bindings.

## 2. Editor/Runtime surfaces
- User-facing: Yes - USD stage actor/runtime components plus Stage Editor, importer/exporter, and schema translators.

## 3. Key Modules

- **USDSchemas** (Runtime) – USD schema translators and utilities for reading/writing prim data.
- **USDStage** (Runtime) – Core runtime representation of opened USD stages, prim twins, and live scene updates.
- **USDStageEditor** (Editor) – UI and tools for browsing stages, prim trees, and live editing.
- **USDStageImporter** (Editor) – Import pipeline for USD assets into Unreal content.
- **USDStageEditorViewModels** (Editor) – View models for the Stage Editor UI.
- **USDExporter** (Editor) – Export pipeline for writing USD from Unreal actors/assets.
- **USDClassesEditor** (Editor) – Editor extensions for USD-specific asset types.
- **GeometryCacheUSD** (Editor) – Geometry cache streaming/export utilities tied to USD.
- **USDTests** (Editor) – Test coverage for USD workflows.

## 4. Important Types & APIs

### `AUsdStageActor`

- Role: Runtime actor that opens a USD stage and spawns Unreal components/assets to represent USD prims.
- Key properties: `RootLayer`, `StageState`, `AssetCache` (`UUsdAssetCache3`), `InitialLoadSet`, `InterpolationType`, `PurposesToLoad`, `KindsToCollapse`, `bMergeIdenticalMaterialSlots`, `bShareAssetsForIdenticalPrims`, `NaniteTriangleThreshold`, render context/material purpose selection.
- Behavior: Drives import options (collapsing, instancing, geometry cache handling) and holds caches/link data (`UUsdInfoCache`, `UUsdPrimLinkCache`).

### `UGeometryCacheUsdComponent`

- Role: Component that renders USD geometry cache data directly as a `UGeometryCacheComponent`.
- Use when streaming time-varying mesh data from USD without baking to static assets.

### `UUsdStageEditorSettings` (editor-only)

- Role: Editor settings backing the USD Stage Editor UI; controls default behaviors when attaching the editor to a stage actor.

### Export/import helpers

- `UUsdConversionBlueprintContext` exposes common component types (lights, cameras, mesh components) to USD export pipelines.
- Various translator utilities under `USDSchemas` handle schema-specific conversions (meshes, lights, materials, media audio, volumes, etc.).

## 5. Typical usage patterns

- Enable USD Importer (also pulls in USD Core). In the editor, add an `USD Stage Actor` to a level and point `RootLayer` at a `.usd/.usda/.usdc/.usdz` file.
- Adjust import behavior on the actor (load set, interpolation, collapsing, Nanite threshold, material/render context) before opening the stage.
- Use the USD Stage Editor to inspect the prim tree, trigger imports/exports, and edit prim metadata; USDStageImporter handles asset generation into your project.
- For playback of animated caches, add `UGeometryCacheUsdComponent` or rely on stage actor-generated components.
- Export back to USD via USDExporter tools from the editor modules.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
