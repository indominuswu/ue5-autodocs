# Plugin Audit Plugin Overview

## 1. What this plugin does

- Editor-only tool that audits how plugins reference each other and surfaces connectivity information.
- Provides a browser tab to inspect plugin metadata, dependency edges, and status at a glance.
- Useful for validating plugin isolation and detecting unexpected plugin coupling before distribution.

## 2. Key Modules

- **PluginAudit** (Editor)  
  - Role: Slate-based UI (`SPluginAuditBrowser`) and module startup wiring for the audit tab/panel.

## 3. Important Types & APIs

### `SPluginAuditBrowser`

- Role: Slate widget that displays plugin dependency information in table form.
- Key behavior: Collects plugin descriptors, renders audit rows, and supports filtering/sorting.

### `FPluginAuditModule`

- Role: Editor module that registers the audit UI and drives refresh actions.
- Key behavior: Initializes/tears down the audit tab and gathers data from plugin descriptors.

## 4. Typical usage patterns

- Enable the plugin, then open the Plugin Audit tab (via Developer Tools/Window menus) to review plugin dependency data.
- Use it during plugin development to ensure dependencies are intentional and to spot missing required modules before packaging.
- No runtime impact; it only runs in the editor.

## 5. Version-specific notes (UE 5.7)

- Marked experimental and disabled by default in UE 5.7.
- No explicit 5.7-specific changes noted.
