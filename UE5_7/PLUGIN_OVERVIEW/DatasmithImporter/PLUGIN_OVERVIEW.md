# Datasmith Importer Plugin Overview

## 1. What this plugin does

- Core Datasmith import pipeline for `.udatasmith` scenes and live Direct Link sources.
- Provides translators, external source handling, and editor tooling to ingest scenes into Unreal.
- Manages import contexts, reimport, asset factories, and Direct Link extensions.

## 2. Key Modules

- **DatasmithExternalSource** / **ExternalSource** (Runtime) – Abstractions for Datasmith sources (files, Direct Link endpoints) and utilities to resolve/import them.
- **DatasmithTranslator** / **DatasmithNativeTranslator** (Runtime) – Translator framework and native translators used by the importer.
- **DatasmithImporter** (Editor) – Editor-facing importer implementation, dialogs, and asset factories.
- **DirectLinkExtension** (Runtime) / **DirectLinkExtensionEditor** (Editor) – Direct Link support and editor integration.
- **DirectLinkTest** (Runtime) – Test helpers for Direct Link workflows.

## 3. Important Types & APIs

- `FDatasmithImporter` / `FDatasmithImporterImpl` – Main import controller that creates assets, actors, and metadata from Datasmith scenes.
- `FDatasmithImportContext` – Holds import options, paths, and asset references while translating a scene.
- `UDatasmithImportOptions` / `UDatasmithImporterEditorSettings` – User-configurable import settings (geometry, materials, reimport behavior).
- `FDatasmithDirectLinkTranslator` and `FDatasmithDirectLinkExternalSource` – Bridge live Direct Link streams into the Datasmith importer.
- `FDatasmithFileProducer` / `FDatasmithFileUriResolver` – Handle locating and validating file-based sources before translation.
- Editor helpers such as `FActorFactoryDatasmithScene` and `UDatasmithDataprepOperation` – Spawn imported scenes and hook into Dataprep workflows.

## 4. Typical usage patterns

- Enable Datasmith Importer (and required translators) then import `.udatasmith` files through the Content Browser or drag-drop; choose options in the Datasmith import dialog backed by `UDatasmithImportOptions`.
- Use Direct Link to stream changes from DCC tools; `DirectLinkExtension` keeps sources synced and `FDatasmithImportContext` manages reimport actions.
- Leverage Dataprep operations/fetchers included with the importer for automated cleanup or asset processing during import.
- Imported scenes create assets (meshes, materials, lights, sequences) and actors in the level, with reimport paths preserved via external source records.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
