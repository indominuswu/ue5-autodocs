# PSD Importer Material Designer Bridge Plugin Overview

## 1. What this plugin does

- Editor-only bridge that converts PSD Importer documents into Material Designer assets.
- Provides factories to generate Material Designer materials/quads directly from PSD documents and layers.
- Designed to streamline turning PSD art into Material Designer graphs/content.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor factories (`UPSDImporterMDMaterialFactory`, `UPSDImporterMDQuadsFactory`) that artists use to import PSDs straight into Material Designer assets.

## 3. Key Modules

- **PSDImporterMaterialDesignerBridge** (Editor)  
  - Role: Import factories that target Material Designer asset types using PSD data.
  - Notable types: `UPSDImporterMDMaterialFactory`, `UPSDImporterMDQuadsFactory`.

## 4. Important Types & APIs

### `UPSDImporterMDMaterialFactory`

- Role: Creates Material Designer material assets from PSD documents/layers.
- Behavior: Consumes `UPSDDocument` data during import to populate material inputs.

### `UPSDImporterMDQuadsFactory`

- Role: Generates Material Designer quad assets based on PSD documents.
- Behavior: Maps PSD layers onto quad resources during import.

## 5. Typical usage patterns

- Enable both PSD Importer and Material Designer, then import PSD files using the bridge factories to create Material Designer assets.
- Choose the Material Designer target (material or quads) during import to automatically wire PSD layers into the generated assets.
- Editor-only; no runtime footprint.

## 6. Version-specific notes (UE 5.7)

- Experimental and disabled by default.
- No explicit UE 5.7-specific notes in source; behavior matches current implementation.

