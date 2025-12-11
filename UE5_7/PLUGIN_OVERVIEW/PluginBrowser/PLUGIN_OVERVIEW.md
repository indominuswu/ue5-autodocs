# Plugin Browser Plugin Overview

## 1. What this plugin does
- Adds the Plugins window for enabling/disabling plugins and creating new ones from templates.
- Provides UI for editing plugin metadata (descriptor fields, categories, paths) and for installing sample templates.
- Relies on PluginUtils for underlying creation/editing helpers.

## 2. Key Modules
- **PluginBrowser** (Editor)  
  - Role: Main UI, commands, plugin wizard, and descriptor editing.  
  - Notable types: `FPluginBrowserModule`, `IPluginBrowser`, `IPluginWizardDefinition`, `FDefaultPluginWizardDefinition`, `UPluginMetadataObject`, `SPluginBrowser`.

## 3. Important Types & APIs
### `FPluginBrowserModule`
- Role: Registers the Plugins window, commands, and wizard definitions.
- Key functions: spawn plugin browser tab, open plugin creation wizard, refresh plugin lists/categories.

### `IPluginWizardDefinition` and `FDefaultPluginWizardDefinition`
- Role: Define how plugin templates are presented and instantiated (content copying, descriptor population).

### `UPluginMetadataObject`
- Role: UObject wrapper around `.uplugin` metadata for editing within details panels.
- Key properties: friendly name, description, category, modules, marketplace/support URLs.

## 4. Typical usage patterns
- Open **Edit → Plugins** to manage installed plugins, enable/disable them, and view descriptions.
- Use the “New Plugin” wizard to choose a template, set descriptor fields, and create a new plugin scaffold (powered by PluginUtils).
- Edit plugin metadata through the details panel; changes are written back to the `.uplugin` file.

## 5. Version-specific notes (UE 5.7)
- No UE 5.7-specific changes noted; plugin is stable and ships enabled by default.
