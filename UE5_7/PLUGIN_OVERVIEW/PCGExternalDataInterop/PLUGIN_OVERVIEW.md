# Procedural Content Generation Framework (PCG) External Data Interop Plugin Overview

## 1. What this plugin does
- Extends PCG with nodes for ingesting external Alembic data into PCG graphs.
- Adds Blueprint helper functions to export/import Alembic files into PCG data assets.
- Ships with editor tooling for asset export and default setups (e.g., City Sample handedness/scale).

## 2. Editor/Runtime surfaces

- User-facing: Yes - Adds the `LoadAlembic` PCG node and Blueprint helpers (`UPCGLoadAlembicFunctionLibrary`) that users run to import/export Alembic data into PCG assets.

## 3. Key Modules
- **PCGExternalDataInterop** (Runtime)  
  - Role: Runtime PCG node implementation for loading Alembic data.
- **PCGExternalDataInteropEditor** (Editor)  
  - Role: Editor-only exporters and Blueprint helper library for authoring Alembic-to-PCG workflows.

## 4. Important Types & APIs
- `UPCGLoadAlembicSettings` (`PCGExternalDataInterop`)  
  - Role: PCG node settings for importing an Alembic file; overrides node name/title/tooltips.  
  - Key properties: `AlembicFilePath`, `ConversionScale`, `ConversionRotation`, `bConversionFlipHandedness`, optional `Setup` preset.  
  - Functions: `SetupFromStandard` helper to apply preset import transforms and attribute mappings.
- `FPCGLoadAlembicElement` (`PCGExternalDataInterop`)  
  - Role: PCG element that performs dependency hashing, prepares, and executes Alembic loading into PCG data.
- `UPCGLoadAlembicFunctionLibrary` (`PCGExternalDataInteropEditor`)  
  - Role: Blueprint callable helpers for exporting Alembic data into PCG assets or collections.  
  - Key functions: `ExportAlembicFileToPCG`, deprecated `LoadAlembicFileToPCG`, `SetupFromStandard`.
- `UPCGAssetExporter` subclass `UPCGAlembicToPCGAssetExporter`  
  - Role: Handles serialization of Alembic-derived PCG assets with customizable metadata.

## 5. Typical usage patterns
- Enable the plugin alongside `PCG` and `AlembicImporter`.
- Add a PCG node “LoadAlembic” to a graph to pull geometry from an `.abc` file, adjusting conversion scale/rotation or preset setup.
- From Blueprint or editor utilities, call `ExportAlembicFileToPCG` to bake Alembic content into a `UPCGDataAsset`.
- Use attribute mappings to bind Alembic data streams into PCG attribute selectors.

## 6. Version-specific notes (UE 5.7)
- Marked beta and experimental in the `.uplugin`.
- No explicit UE 5.7-specific changes noted; overview matches current 5.7 source.

