# Editor Scripting Utilities Plugin Overview

## 1. What this plugin does

- Exposes editor-only Blueprint/script libraries for asset, level, mesh, dialog, and filtering operations.
- Provides helper functions to script editor workflows without writing C++.
- Beta and disabled by default.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor Blueprint libraries for asset/level/mesh/dialog/filter scripting.

## 3. Key Modules

- **EditorScriptingUtilities** (Editor, Default)  
  - Role: Blueprint libraries and utilities for editor scripting.  
  - Notable types: `UEditorAssetLibrary`, `UEditorLevelLibrary`, `UEditorStaticMeshLibrary`, `UEditorSkeletalMeshLibrary`, `UEditorDialogLibrary`, `UEditorFilterLibrary`, `FEditorScriptingUtilitiesModule`, `EditorScriptingUtils`.

## 4. Important Types & APIs

- Asset operations: `UEditorAssetLibrary` (load/save/delete/move/duplicate), path utilities, metadata access.  
- Level operations: `UEditorLevelLibrary` (spawn/destroy actors, select, set transforms, level streaming utilities).  
- Mesh operations: `UEditorStaticMeshLibrary`, `UEditorSkeletalMeshLibrary` for importing/editing mesh data.  
- Dialogs: `UEditorDialogLibrary` for message dialogs.  
- Filtering: `UEditorFilterLibrary` helpers for asset filtering.  
- Utilities: `EditorScriptingUtils` shared helpers.

## 5. Typical usage patterns

- Enable the plugin, then use the Blueprint libraries to build editor automation tools (batch asset edits, level manipulation, mesh processing).  
- Combine with Editor Utility Blueprints to expose scripted workflows to users.

## 6. Version-specific notes (UE 5.7)

- Beta/off by default; no explicit 5.7-specific changes noted.
