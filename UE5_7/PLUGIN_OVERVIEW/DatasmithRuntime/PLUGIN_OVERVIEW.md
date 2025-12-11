# Datasmith Runtime Plugin Overview

## 1. What this plugin does

- Enables loading and updating Datasmith scenes at runtime (outside the editor).
- Provides Blueprint and C++ APIs to stream Datasmith files or Direct Link sources into a running game.
- Handles translation, material selection, and scene instancing without editor-only dependencies.

## 2. Key Modules

- **DatasmithRuntime** (Runtime) – Runtime importer, Direct Link receiver, material selection, and Blueprint helper library.

## 3. Important Types & APIs

- `ADatasmithRuntimeActor` – Runtime actor that owns imported Datasmith content and drives translation/update jobs.
- `DatasmithRuntime::FSceneImporter` – Performs translation of Datasmith scenes into runtime components and meshes.
- `UDatasmithRuntimeBlueprintLibrary` – Blueprint utilities to enumerate sources, start imports, and manage runtime Datasmith actors.
- `FDatasmithRuntimeMaterialSelector` / `MaterialImportUtils` – Choose and build materials during runtime translation.
- `FDatasmithRuntimeAuxiliaryData` and `FDatasmithRuntimeUtils` – Helper structures for tracking imported elements and utilities for scene updates.
- `DirectLinkUtils` – Supports Direct Link scene receiver interactions at runtime.

## 4. Typical usage patterns

- Enable the plugin in a runtime project that needs to stream Datasmith content; spawn or reference `ADatasmithRuntimeActor`.
- Use `UDatasmithRuntimeBlueprintLibrary` to start imports from a Datasmith file or available Direct Link sources, then track completion via returned handles.
- Configure tessellation/material options up front (e.g., through `UDatasmithImportOptions`) before triggering translation.
- Update or reimport content at runtime by reissuing translation jobs; the actor applies additions/updates/deletions to the existing scene.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
