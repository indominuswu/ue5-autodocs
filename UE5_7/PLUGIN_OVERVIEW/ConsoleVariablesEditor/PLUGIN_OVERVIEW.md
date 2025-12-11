# Console Variables Editor Plugin Overview

## 1. What this plugin does

- Provides an editor panel to view, filter, save, load, and synchronize console variables (cvars).
- Supports Concert multi-user sync of cvar states and presets; ships a runtime asset type for storing cvar sets.
- Beta and disabled by default.

## 2. Key Modules

- **ConsoleVariablesEditor** (UncookedOnly, Default, Editor)  
  - Role: Main UI, commands, styles, asset actions/factory, multi-user sync.  
  - Notable types: `FConsoleVariablesEditorModule`, `UConsoleVariablesEditorFunctionLibrary`, `FConsoleVariablesEditorCommandInfo`, `SConsoleVariablesEditorMainPanel`, `SConsoleVariablesEditorList`/`Row`/`ValueInput`, filters (`IConsoleVariablesEditorListFilter` and implementations), `AssetTypeActions_ConsoleVariables`, `UConsoleVariablesEditorFactory`, `FConsoleVariablesEditorProjectSettings`, multi-user (`FConsoleVariableSync`, `FConcertConsoleVariableSessionCustomization`).

- **ConsoleVariablesEditorRuntime** (Runtime, Default)  
  - Role: Runtime asset for cvar presets and module registration.  
  - Notable types: `UConsoleVariablesAsset`, `FConsoleVariablesEditorRuntimeModule`.

## 3. Important Types & APIs

- UI widgets: `SConsoleVariablesEditorMainPanel`, `SConsoleVariablesEditorList`/`Row`, `SConsoleVariablesEditorCustomConsoleInputBox`, global search toggle, tooltips.  
- Filters: show-only modified/commands/variables, set-by-current-preset, set-in-session, source filters.  
- Assets: `UConsoleVariablesAsset` stores cvar key/value sets; factory and asset actions enable creation/editing.  
- Multi-user: `FConsoleVariableSync` and Concert customizations synchronize cvars across sessions.  
- Commands & style: `FConsoleVariablesEditorCommandInfo`, `FConsoleVariablesEditorStyle`.

## 4. Typical usage patterns

- Enable the plugin; open the Console Variables Editor panel to inspect and edit cvars, apply filters, and save/load presets as `ConsoleVariablesAsset`.  
- Use Concert sync to share cvar changes during multi-user sessions.  
- Run presets at runtime using `UConsoleVariablesAsset` (Runtime module).

## 5. Version-specific notes (UE 5.7)

- Beta/off by default; no explicit 5.7-specific changes noted.
