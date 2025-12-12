# Blank Example Plugin Overview

## 1. What this plugin does

- Minimal template plugin demonstrating the structure of a runtime module.
- Intended as a starting point for custom plugins; exposes only the standard module interface helpers.
- Disabled by default to avoid adding unused code.

## 2. Editor/Runtime surfaces
- User-facing: No - Template module with no gameplay/editor functionality beyond the standard module interface helpers.

## 3. Key Modules

- **BlankPlugin** (Runtime, Default)  
  - Role: Barebones runtime module with no gameplay features; provides module load/availability helpers.  
  - Notable types: `IBlankPlugin`, internal module implementation in `BlankPlugin.cpp`.

## 4. Important Types & APIs

### `IBlankPlugin`

- Role: Public module interface; offers `Get()` and `IsAvailable()` to access the `BlankPlugin` module.
- Notes: No additional APIs or gameplay types are defined.

## 5. Typical usage patterns

- Enable the plugin, duplicate/rename it, and extend the module with your own code as a bootstrap for new plugins.
- Use `IBlankPlugin::Get()` only after confirming `IsAvailable()` if accessing the module during runtime/editor.

## 6. Version-specific notes (UE 5.7)

- No UE 5.7-specific functionality; this is a baseline template module in the 5.7 source tree.

