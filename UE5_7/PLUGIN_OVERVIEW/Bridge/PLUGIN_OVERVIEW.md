# Bridge Plugin Overview

## 1. What this plugin does

- Integrates Quixel Bridge/Megascans with Unreal, enabling browsing and importing Megascans assets directly in the editor.
- Handles communication with the Bridge process, drag-and-drop import, and automated material/texture setup.
- Provides editor settings for Megascans directories and import preferences.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor UI/panel for Megascans plus import factories (`UImportFactory`, `FAssetsImportController`) and settings (`UMSSettings`) for artists to bring in Quixel assets.

## 3. Key Modules

- **Bridge** (Editor)  
  - Role: UI, communication, and utilities for Bridge integration.
- **MegascansPlugin** (Editor)  
  - Role: Asset import controllers, factories, and settings for Megascans content.

## 4. Important Types & APIs

- Bridge comms & UI: `FBridgeUIManager`, `FNodeCommManager`, `FNodeProcess`, `FNodeProcessRunnableThread`, `FNodePort`, `FBrowserBinding`.
- Import pipeline: `FAssetsImportController`, `UImportFactory`, `FProgressiveImport3D`, `FProgressiveImportSurfaces`, `FBlendMaterials`, `FMaterialUtils`, `UMSAssetImportData`.
- Settings & helpers: `UMSSettings`, `FVersionInfoHandler`, `FBridgeDragDropHelper`, `FBridgeDragDropUtils`, `FTCPServer`.
- Module interfaces: `IBridgeModule`, `IMegascansLiveLinkModule`.

## 5. Typical usage patterns

- Enable the plugin; use the Bridge panel to browse Megascans assets or drag assets from the Bridge app into the editor.
- Configure paths and preferences in Megascans settings (`UMSSettings`), including default material setups.
- Imports run through `UImportFactory` and related helpers to create materials, textures, and meshes with Megascans-specific conventions.
- Live-link communication between Bridge and Unreal is managed by the Node/Port/TCP helpers; no runtime gameplay dependencies.

## 6. Version-specific notes (UE 5.7)

- Enabled by default as the Megascans integration for UE 5.7.
- No explicit UE 5.7-specific notes found; overview reflects the current integration.

