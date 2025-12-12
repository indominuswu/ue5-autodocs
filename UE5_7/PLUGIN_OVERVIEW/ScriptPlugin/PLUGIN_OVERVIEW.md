# Script Plugin Overview

## 1. What this plugin does

- Serves as an example/script template plugin for adding custom scripting support to Unreal.
- Provides a minimal Script asset type, factories for import/reimport, and Blueprint integration hooks.
- Offers context/components that can host script instances at runtime.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Script asset factories and Blueprint integration plus runtime script context/components.

## 3. Key Modules

- **ScriptPlugin** (Runtime, PreDefault)  
  - Role: Core Script asset/runtime support, context handling, and component wrappers.
- **ScriptEditorPlugin** (Editor)  
  - Role: Editor asset factories, generated class handling, and integration with Blueprint tooling.

## 4. Important Types & APIs

### Asset and runtime types

- `UScriptBlueprint` / `UScriptBlueprintGeneratedClass`: Blueprint types representing a Script asset and its generated class.
- `UScriptContext` / `UScriptContextComponent` / `UScriptPluginComponent`: Hosts a Script instance, enabling it to run alongside actor components.

### Factories

- `UScriptFactory`, `UReimportScriptFactory`: Import/reimport Script assets for editing in the editor.

## 5. Typical usage patterns

- Use this plugin as a starting point for building a custom scripting integration.
- Import or create Script assets through the provided factories; the editor module will generate `UScriptBlueprint` assets.
- Attach `UScriptContextComponent` or `UScriptPluginComponent` to actors to run script instances at runtime.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
