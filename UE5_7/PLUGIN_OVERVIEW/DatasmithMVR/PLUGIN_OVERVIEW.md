# Datasmith MVR Plugin Overview

## 1. What this plugin does

- Adds Datasmith translator support for `.udatasmith` files containing My Virtual Rig (MVR) lighting data.
- Converts MVR fixture information into Unreal/DMX-compatible assets during Datasmith import.
- Exposes import options specific to MVR content.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Datasmith users enable this to import MVR lighting data, configure `UDatasmithMVRImportOptions`, and generate DMX-ready fixtures during import.

## 3. Key Modules

- **DatasmithMVRTranslator** (Editor) – Translator module that detects MVR content inside Datasmith scenes and converts it during import.

## 4. Important Types & APIs

- `FDatasmithMVRTranslator` – Implements Datasmith translation of MVR payloads, mapping fixtures and related data into Unreal assets.
- `UDatasmithMVRImportOptions` – Import-time settings for MVR-aware Datasmith imports.
- `IDatasmithMVRTranslatorModule` – Module interface for accessing the translator programmatically.

## 5. Typical usage patterns

- Enable Datasmith Importer and Datasmith MVR; import `.udatasmith` files generated with MVR content.
- Configure `UDatasmithMVRImportOptions` to control how fixtures and DMX-related data are mapped on import.
- Imported scenes will include converted fixtures compatible with the DMX toolset, ready for pixel mapping or control console workflows.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

