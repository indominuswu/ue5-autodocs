# Dataprep Editor Plugin Overview

## 1. What this plugin does

- Provides the Dataprep Editor, simplifying creation and execution of data preparation pipelines inside Unreal Editor.
- Includes core libraries and scripting utilities for Dataprep assets, filters, and operations.
- Extends the editor with UI, viewport, and scripting hooks tailored to Dataprep workflows.

## 2. Key Modules

- **DataprepEditor** (Editor)  
  - Role: Main editor UI, widgets, and viewport integration for Dataprep assets.
- **DataprepCore** (Editor)  
  - Role: Core Dataprep asset and pipeline logic.
- **DataprepLibraries** (Editor)  
  - Role: Libraries of Dataprep operations and selection transforms.
  - Notable types: Operations in `DataprepEditingOperations`, `DataprepSelectionTransforms`.
- **DataprepEditorScriptingUtilities** (Editor)  
  - Role: Blueprint/automation helpers for interacting with Dataprep assets.
  - Notable types: `UEditorDataprepAssetLibrary`.

## 3. Important Types & APIs

### `UEditorDataprepAssetLibrary`
- Role: Blueprint-exposed utilities for creating and manipulating Dataprep assets via scripts.
- Key functions: Asset creation, pipeline execution, and utility methods for Dataprep pipelines.

### Dataprep operation/transform classes
- Role: Implement built-in filters and transforms (`DataprepEditingOperations`, `DataprepSelectionTransforms`).
- Key behavior: Operate on actor/asset selections during pipeline execution.

### Dataprep editor widgets (`SDataprepEditorViewport`, etc.)
- Role: Custom Slate widgets providing viewport and editing UI for Dataprep assets.

## 4. Typical usage patterns

- Enable the plugin (and required Dataprep dependencies) to author Dataprep assets in the editor.
- Use the Dataprep Editor to assemble pipelines from provided operations and transforms, previewing results in the viewport.
- Script Dataprep workflows with `UEditorDataprepAssetLibrary` for automation or batch processing.

## 5. Version-specific notes (UE 5.7)

- Plugin is disabled by default; no UE 5.7-specific changes noted beyond current module layout.
