# Datasmith FBX Importer Plugin Overview

## 1. What this plugin does

- Extends Datasmith to import scenes produced by DeltaGen and VRED through FBX payloads.
- Handles variant sets, materials, animations, and auxiliary data specific to automotive design tools.
- Provides import options and scene processors tailored to DeltaGen/VRED conventions.

## 2. Key Modules

- **DatasmithVREDTranslator** (Editor) – Translator for VRED-originated content.
- **DatasmithDeltaGenTranslator** (Editor) – Translator and material selector for DeltaGen scenes.
- **DatasmithFBXTranslator** (Editor) – Shared FBX parsing and scene preparation utilities used by the above translators.

## 3. Important Types & APIs

- `FDatasmithFBXImporter` / `FDatasmithFBXScene` – Core FBX scene reader used by the translators.
- `FDatasmithDeltaGenTranslator` with helpers like `FDatasmithDeltaGenSceneProcessor` and `FDatasmithDeltaGenAnimationInterpolator` – Convert DeltaGen-specific scene data, animations, and variants.
- `FDatasmithVREDTranslator` / `FDatasmithVREDClipProcessor` – Handle VRED clip/variant conversion and material processing.
- `UDatasmithFBXImportOptions` and `UDatasmithDeltaGenImportOptions` – Editor-facing settings to control variant handling, materials, and geometry import for these workflows.
- Utility classes such as `FDatasmithFBXHashUtils` and `FDatasmithFBXImporterLog` – Aid deduplication and diagnostics during import.

## 4. Typical usage patterns

- Enable Datasmith Importer and this plugin, then import DeltaGen/VRED FBX exports through the Content Browser or Datasmith import dialog.
- Configure options (e.g., variant import, animation interpolation, material selection) via the provided import settings objects.
- Translators reconstruct scene hierarchy, materials, and variants into Datasmith assets for further editing or rendering inside Unreal.
- Use the generated Datasmith scene to drive automotive visualization workflows alongside Datasmith content and area lights.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
