# USD Importer MDL integration Plugin Overview

## 1. What this plugin does

- Extends USD Importer so USD stages that reference MDL materials can be imported and rendered in Unreal.
- Provides a USD Shade material translator specialized for the MDL render context.
- Relies on the MDL Importer, USD Core, and USD Importer plugins.

## 2. Editor/Runtime surfaces

- User-facing: Yes - USD material translator (`FMdlUsdShadeMaterialTranslator`) that lets users import USD stages with MDL materials into Unreal via USD Importer.

## 3. Key Modules

- **USDImporterMDL** (Editor)  
  - Role: Registers the MDL-aware USD material translator that converts MDL-bound USD materials during import/export flows.
  - Notable types: `FMdlUsdShadeMaterialTranslator` (extends `FMaterialXUsdShadeMaterialTranslator`).

## 4. Important Types & APIs

### `FMdlUsdShadeMaterialTranslator` (editor-only)

- Role: USD Shade translator that recognizes the MDL render context and creates Unreal assets accordingly.
- Key behavior: Overrides `CreateAssets()` to emit assets/material graphs suited to MDL references. Deprecated static `MdlRenderContext` alias indicates migration to `UnrealIdentifiers::MdlRenderContext`.

## 5. Typical usage patterns

- Enable USD Importer MDL alongside USDImporter, USDCore, and MDLImporter.
- Open/import USD stages that contain MDL material references; the translator will generate Unreal materials that respect the MDL bindings.
- Use with the USD Stage Actor and Stage Editor—material translation happens during USD import/export; no runtime API calls are typically required.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

