# Alembic Importer Plugin Overview

## 1. What this plugin does
- Imports general Alembic (`.abc`) geometry/transform caches into Unreal.
- Provides editor factories, options, and utilities for mesh and camera data.
- Includes commandlet support for testing/conversion and a shared Alembic library module.

## 2. Key Modules
- **AlembicImporter** (Editor)
  - Role: Main importer, factories, UI customizations, and utilities for Alembic assets.
- **AlembicLibrary** (Editor)
  - Role: Shared Alembic reader/writer functionality used by the importer.

## 3. Important Types & APIs

### `UAlembicImportFactory`
- Role: Content Browser factory that handles Alembic file import.

### `UAlembicImportOptions` / `FAbcImportSettings`
- Role: User-configurable options controlling sampling, conversion, compression, and material settings.

### Core reader types
- `FAbcImporter`, `FAbcFile`, `FAbcObject`, `FAbcPolyMesh`, `FAbcTransform` — parse Alembic files and expose mesh/transform data.
- `FAbcImportUtilities` provides helper functions for sampling and conversion.

### Editor helpers
- `FAlembicImporterModule`, `FAlembicLibraryModule` manage module startup; `UAbcImportSettingsCustomization` customizes option UI; `UAlembicTestCommandlet` supports testing.

## 4. Typical usage patterns
- Import an Alembic file via Content Browser; choose options in the Alembic Import dialog (`UAlembicImportOptions`).
- Use sampling and track selection controls to decide which frames and objects are imported.
- Resulting assets may include static meshes, geometry caches, and associated import data.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.