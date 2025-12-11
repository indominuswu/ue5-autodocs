# AxF Importer Plugin Overview

## 1. What this plugin does

- Imports AxF (Appearance Exchange Format) material files into Unreal.
- Converts AxF material parameters into Unreal material assets and supporting textures.
- Editor-only workflow; adds a Content Browser factory and options UI for AxF files.

## 2. Key Modules

- **AxFImporter** (Editor)  
  - Role: AxF import pipeline, material creation, and editor UI for import options.

## 3. Important Types & APIs

- `FAxFImporterModule`: Module entry registering the importer and UI.
- `UAxFImporterFactory`: Content Browser factory that recognizes `.axf` files and triggers import.
- `FAxFFileImporter`: Core AxF file parser and material builder.
- `UAxFImporterOptions` / `FAxFOptionsWindow`: User-configurable import options (e.g., texture generation, material variants).
- `FAxFImporter`: Helper for driving the import process and logging.

## 4. Typical usage patterns

- Enable the plugin, then drag/drop or right-click import `.axf` files in the Content Browser.
- Configure import behavior in the AxF options dialog (`UAxFImporterOptions`) before finalizing the import.
- Resulting materials and textures are generated under the chosen content path; adjust them like standard Unreal materials.

## 5. Version-specific notes (UE 5.7)

- Disabled by default and part of the Enterprise toolset.
- No explicit UE 5.7-specific notes found; overview is based on the current code.
