# Fab Plugin Overview

## 1. What this plugin does
- Integrates the Fab content platform into the editor for browsing, downloading, and importing assets (including Megascans and Marketplace items).
- Uses Interchange pipelines to convert downloaded content into Unreal assets with editor-side workflows.
- Provides authentication, download management, and import workflows tailored to Fab asset types.
- Adds editor UI (browser, settings panels, notifications) to manage accounts and asset ingest.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor-facing browser/download/import workflows, settings, and Interchange pipelines for users to pull Fab content into projects.

## 3. Key Modules
- **Fab** (Editor)
  - Role: All editor-facing functionality—authentication, asset browsing, download pipeline, and Interchange-based importing.
  - Notable types: `FFabAuthentication`, `FFabBrowser`, `FFabDownloadRequest`, `UFabSettings`, `FFabWorkflowFactoryRegistry`, `UInterchangeMegascansPipeline`.

## 4. Important Types & APIs

### `FFabAuthentication`
- Role: Handles user sign-in/token management against Fab services.
- Key behavior: Manages auth state for downstream download and browser requests.

### `FFabBrowser` / `FFabBrowserApi`
- Role: Editor UI and HTTP client for querying Fab content and showing search/browse results.
- Integrates with notification progress widgets to report download/import status.

### `FFabDownloadRequest`
- Role: Orchestrates asset downloads via HTTP or BuildPatchServices; exposes progress and completion delegates.
- Key properties: `EFabDownloadType` (HTTP vs BuildPatch), `FFabDownloadStats` with percent/bytes/speed and file list.

### `UFabSettings` / `FFabSettingsCustomization`
- Role: Editor project settings for Fab (endpoints, download paths, account toggles).
- Customization hooks provide tailored settings UI under Plugins → Fab.

### Interchange pipeline & import helpers
- `UInterchangeMegascansPipeline`, `UInterchangeInstancedFoliageTypeFactoryNode`, `UInterchangeInstancedFoliageTypeFactory` convert Fab/Megascans payloads to engine assets.
- Workflow utilities such as `FFabWorkflow`, `FFabWorkflowFactory`, `FGenericImportWorkflow`, and drag-drop helpers (`FFabDragDropOp`, `FGenericDragDropWorkflow`) define how assets are staged and imported.

## 5. Typical usage patterns
- Enable Fab and ensure Interchange is active (declared dependency). Configure credentials and download locations in `Project Settings → Plugins → Fab`.
- Browse/search Fab assets inside the editor browser; start downloads and monitor `NotificationProgressWidget` feedback.
- Drag-drop search results into the content browser or viewport; importers and pipelines (e.g., Megascans, MetaHuman, foliage) convert payloads into native assets and can place actors via `FActorSpawner`.
- Use download APIs to track progress or integrate custom workflows; BuildPatchServices is used automatically for Marketplace downloads when required.

## 6. Version-specific notes (UE 5.7)
- Plugin targets UE 5.7 (`EngineVersion` 5.7.0) and is editor-only. No additional 5.7-specific flags beyond standard dependencies were found.

