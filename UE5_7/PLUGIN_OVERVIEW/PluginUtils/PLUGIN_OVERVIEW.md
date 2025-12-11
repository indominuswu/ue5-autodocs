# Plugin Utilities Plugin Overview

## 1. What this plugin does
- Supplies helper APIs for creating and editing plugins from tools like the Plugin Browser.
- Automates descriptor generation, template copying, module list updates, and plugin validation.
- Intended for editor tooling; not loaded at runtime or in cooked builds.

## 2. Key Modules
- **PluginUtils** (Editor)  
  - Role: Utility functions for plugin creation/editing used by other editor tools.  
  - Notable types: static helpers in `PluginUtils.h` for generating plugin descriptors, copying template content, and updating module metadata.

## 3. Important Types & APIs
### `UE::PluginUtils` (functions in `PluginUtils.h`)
- Role: Namespace of helper routines for plugin lifecycle tasks.
- Key functions: descriptor creation/population, updating modules/targets, copying template assets/code, performing validation and filesystem operations for new plugins.

## 4. Typical usage patterns
- Triggered indirectly from the Plugin Browser or other editor automation to scaffold new plugins or modify existing descriptors.
- Call the helper functions from editor-only code or automation scripts to generate `.uplugin` files and associated source/content folders.

## 5. Version-specific notes (UE 5.7)
- No UE 5.7-specific behaviors are documented; functionality is editor-only and metadata-driven.
