# TEDS: Editor Data Storage Features Plugin Overview

## 1. What this plugin does
- Adds a collection of experimental editor features built on top of the core TEDS storage system.
- Modules cover content browser integration, actor compatibility, alerts, debugging tools, outliner support, property editor bindings, revision control, query stack UI, settings panels, and typed element bridges.
- Acts as a feature pack that layers UI and workflows on the base Editor Data Storage plugin.

## 2. Key Modules
- **TedsActorCompatibility** (Editor) — Bridges actors/components into the storage schema.
- **TedsAlerts** (Editor) — Alert/notification utilities backed by TEDS.
- **TedsAssetData** (Editor) — Asset metadata integration.
- **TedsContentBrowser** (Editor) — Content Browser extensions.
- **TedsDebugger** (Editor) — Debugging/inspection tools for storage.
- **TedsOutliner** (Editor) — Outliner support driven by TEDS data.
- **TedsPropertyEditor** (Editor) — Property editor bindings for TEDS columns.
- **TedsQueryStack** (Editor) — Query stack UI and execution.
- **TedsRevisionControl** (Editor) — Revision control hooks.
- **TedsSettings** (Editor) — Settings/UI for configuring TEDS behavior.
- **TedsTableViewer** (Editor) — Generic table viewer for storage rows.
- **TedsEverythingPicker** (Editor) — Picker UI backed by storage queries.
- **TedsTypeInfo** (Editor) — Type metadata helpers.
- **TedsTypedElementBridge** (Editor) — Bridges typed elements into TEDS.
- **TedsEditorCompatibility** (Editor) — Additional editor compatibility glue.

## 3. Important Types & APIs
- Settings and subsystems: `UTedsSettings`, `UTedsSettingsEditorSubsystem`, plus helper functions such as `UpdateSettings`, `UnregisterActiveSettings`, and `UnregisterInactiveSettings`.
- Bridges/adapters: Typed element and actor compatibility modules expose processors and column definitions to surface editor data.
- UI: Table viewer, query stack, outliner, and picker widgets consume TEDS queries to display/edit data.

## 4. Typical usage patterns
- Enable along with `EditorDataStorage`; features register themselves to extend editor panels.
- Configure global options via the TEDS settings panel; the editor subsystem keeps settings in sync.
- Use the provided viewers/pickers when inspecting TEDS data, or extend the modules with custom processors if more columns are needed.

## 5. Version-specific notes (UE 5.7)
- Marked experimental; no explicit UE 5.7-specific behavior documented beyond current source state.
