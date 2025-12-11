# Datasmith C4D Importer Plugin Overview

## 1. What this plugin does

- Adds support for importing content from Maxon Cinema 4D into Unreal Engine via Datasmith.
- Implements a C4D translator and importer pipeline specific to Datasmith workflows.
- Disabled by default; intended for DCC-to-Unreal asset import.

## 2. Key Modules

- **DatasmithC4DTranslator** (Runtime)  
  - Role: Datasmith translator implementation for C4D files.
  - Notable types: `FDatasmithC4DImporter`, `FDatasmithC4DImportOptions`, material selector helpers.

## 3. Important Types & APIs

### `FDatasmithC4DImporter`
- Role: Core importer handling C4D scene parsing and Datasmith asset creation.
- Key behavior: Uses Melange SDK guards and translator helpers to build Datasmith scenes.

### `FDatasmithC4DImportOptions`
- Role: Import options struct controlling how C4D data is translated.
- Key properties: Import toggles, material selection preferences.

### Material/asset helpers
- Role: `FDatasmithC4DImporterMaterialSelector` and related utilities to map C4D materials to Unreal assets.

## 4. Typical usage patterns

- Enable the plugin alongside the Datasmith suite when importing C4D scenes.
- Use the Datasmith import dialog to select C4D files; the translator (`DatasmithC4DTranslator`) handles conversion.
- Adjust import options as needed for materials and scene content through the Datasmith UI.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; plugin remains an optional Datasmith importer in this branch.
