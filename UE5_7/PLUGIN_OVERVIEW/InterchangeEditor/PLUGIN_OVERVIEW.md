# Interchange Editor Plugin Overview

## 1. What this plugin does

- Exposes the Interchange import framework inside the Unreal Editor with UI, pipelines, and scripting entry points.
- Provides configurable pipeline assets, translator settings dialogs, and graph inspectors for Interchange data.
- Adds Blueprint-accessible helpers for scripted imports and file picking.
- Editor-only and enabled by default in supported platforms.

## 2. Key Modules

- **InterchangeEditor** (Editor, Default) — Core editor integration, scripting helpers, FBX import data converters.
- **InterchangeEditorPipelines** (Editor, Default) — Editor pipeline implementations and customization UI.
- **InterchangeEditorUtilities** (Editor, Default) — Utility functions and file picker helpers used by the editor UI.
- Dependency: **Interchange** plugin (runtime framework) enabled for Editor/Program targets.

## 3. Important Types & APIs

### Scripting & utilities

- `UInterchangeEditorScriptLibrary` (BlueprintFunctionLibrary) — Scripted entry points for running imports, querying pipelines, and managing import sessions.
- `UInterchangeEditorUtilities` — Utility methods for editor-side helpers and file dialogs.
- `UInterchangeFilePickerGeneric` — File picker implementation used by Interchange import flows.

### Pipelines and configuration

- `UInterchangeEditorPipelineBase` / `UInterchangeEditorBlueprintPipelineBase` — Editor-specific pipeline base classes.
- `UInterchangePipelineConfigurationGeneric` — Pipeline configuration asset used to chain pipelines and configure options.
- `UInterchangeGraphInspectorPipeline` and UI widgets (`SInterchangeGraphInspectorWindow`, `SInterchangePipelineConfigurationDialog`, etc.) for inspecting node graphs and tweaking pipeline settings.

### Factories & assets

- `UInterchangeFbxAssetImportDataConverter` — Converts legacy FBX import data to Interchange-compatible assets.
- Pipeline asset factories (`UInterchangePipelineBaseFactory`, `UInterchangeEditorBlueprintPipelineBaseFactory`, `UInterchangePythonPipelineAssetFactory`) create pipeline assets within the editor.

## 4. Typical usage patterns

- Enable the plugin (default). Use the Interchange import dialogs; they display translator settings and pipeline configuration widgets provided here.
- For scripted imports, call functions on `UInterchangeEditorScriptLibrary` to run imports headlessly or to configure pipelines programmatically.
- Use graph inspector windows to debug translator output and pipeline transformations on node containers.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific notes found; modules are editor-only and rely on the runtime Interchange framework present in this tree.

