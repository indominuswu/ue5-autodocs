# Plugin Template Tool Plugin Overview

## 1. What this plugin does

- Editor-only tool for browsing and managing plugin template content folders.
- Provides a Slate browser to copy/update template assets used when creating new plugins.
- Intended to streamline maintaining curated plugin templates inside the engine tree.

## 2. Key Modules

- **PluginTemplateTool** (Editor)  
  - Role: Registers the template browser tab and loads template metadata.
  - Notable types: `SPluginTemplateBrowser`, `FPluginTemplateToolModule`.

## 3. Important Types & APIs

### `SPluginTemplateBrowser`

- Role: UI widget that lists available plugin templates and drives copy/install actions.
- Key behavior: Reads template folders, filters entries, and exposes buttons to open or duplicate templates.

### `FPluginTemplateToolModule`

- Role: Editor module that spawns the browser tab and hooks it into the editor menus.
- Key behavior: Handles startup/shutdown and provides accessors used by the browser widget.

## 4. Typical usage patterns

- Enable the plugin and open the Plugin Template Tool tab to inspect template folders.
- Use the browser to copy template content into new plugin projects or refresh existing templates.
- The tool is editor-only and has no runtime footprint.

## 5. Version-specific notes (UE 5.7)

- Experimental and disabled by default in UE 5.7.
- No explicit 5.7-specific behaviors observed in source.
