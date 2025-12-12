# PSD Importer Plugin Overview

## 1. What this plugin does

- Imports layered Adobe Photoshop PSD files into Unreal as `UPSDDocument` assets.
- Exposes PSD document metadata and layers to Blueprints and editor tooling.
- Provides import factories and asset definitions to create PSD assets and spawn actors from them.
- Experimental; not enabled by default.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor importers (`UPSDDocumentImportFactory`, `UActorFactoryPSDDocument`) and Blueprint-accessible `UPSDDocument` assets that users create/read when bringing PSD layers into Unreal.

## 3. Key Modules

- **PSDImporter** (Runtime)  
  - Role: Core PSD document asset, layer data handling, and runtime APIs.
  - Notable types: `UPSDDocument`, `UPSDLayerTextureUserData`, `FPSDFileLayer`.
- **PSDImporterCore** (Runtime)  
  - Role: Shared PSD parsing/utility code used during import.
- **PSDImporterEditor** (Editor)  
  - Role: Import/actor factories and asset definitions for PSD documents.
  - Notable types: `UPSDDocumentImportFactory`, `UActorFactoryPSDDocument`, `UAssetDefinition_PSDDocument`.

## 4. Important Types & APIs

### `UPSDDocument`

- Role: UObject asset representing a PSD file and its layers.
- Key functions: `GetDocumentName`, `GetSize`, `GetLayers`, `WereLayersResizedOnImport`, `GetValidLayers`, `GetTextureCount`.
- Notes: BlueprintType, stores import data; friends with importer to populate internal state.

### `UPSDLayerTextureUserData`

- Role: Asset user data that tracks PSD layer names and metadata for generated textures.
- Usage: Attached to textures created from PSD layers to preserve layer provenance.

### Import/editor classes (`UPSDDocumentImportFactory`, `UActorFactoryPSDDocument`, `UAssetDefinition_PSDDocument`)

- Role: Handle importing PSD files, creating assets, and spawning actors that reference PSD documents.

## 5. Typical usage patterns

- Enable the plugin and import a PSD file via the Content Browser; the factory creates a `UPSDDocument` asset and associated textures.
- Use Blueprint accessors on `UPSDDocument` to inspect layers, sizes, and counts; query `GetValidLayers` for layers that can produce textures.
- Add `UActorFactoryPSDDocument` actors if you need to place PSD-driven content in a level.
- `UPSDLayerTextureUserData` can be read to map generated textures back to their source PSD layers.

## 6. Version-specific notes (UE 5.7)

- Experimental in UE 5.7.
- No explicit UE 5.7-specific changes were found in the code reviewed.

