# InstanceDataObject Fixup Tool Plugin Overview

## 1. What this plugin does
- Provides an editor utility panel to redirect or repair loose `InstanceDataObject` property references.
- Integrates with Editor Data Storage (TEDS) queries to locate and update affected assets.
- Experimental tooling for cleaning up instance data after refactors.

## 2. Key Modules
- **InstanceDataObjectFixupTool** (Editor) - Registers the panel, detail customization, and supporting queries.

## 3. Important Types & APIs
### `UInstanceDataObjectFixupTool`
- Role: Tool entry point that coordinates fixup operations and exposes command hooks.

### `FInstanceDataObjectFixupPanel`
- Role: Slate panel presenting search results and fixup actions.

### `FInstanceDataObjectFixupDetailCustomization`
- Role: Customizes details view for the tool settings/options.

### `FInstanceDataObjectFixupToolTedsQueries`
- Role: Helpers for querying Editor Data Storage to find stale references.

## 4. Typical usage patterns
- Enable the plugin (requires `EditorDataStorageFeatures`), open the Fixup Tool panel, and run queries to locate loose `InstanceDataObject` links.
- Use the UI to redirect references to new objects or clean up invalid entries.

## 5. Version-specific notes (UE 5.7)
- Marked Experimental; behavior based on current UE 5.7 implementation.
