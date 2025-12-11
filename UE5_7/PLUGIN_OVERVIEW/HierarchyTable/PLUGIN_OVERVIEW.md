# Hierarchy Table Plugin Overview

## 1. What this plugin does
- Defines a generic Hierarchy Table asset format for structured hierarchical data used by animation features.
- Runtime module manages data access; editor module supplies asset types, factories, and Slate views.
- Experimental plugin enabled when authoring Hierarchy Table assets.

## 2. Key Modules
- **HierarchyTableRuntime** (Runtime) - Core table structures and default type definitions.
- **HierarchyTableEditor** (UncookedOnly) - Asset definition, factory, editors, and Slate widgets for Hierarchy Tables.

## 3. Important Types & APIs
### `FHierarchyTable`
- Role: Core data structure representing the hierarchical table; supports default type registration.

### `FDefaultHierarchyTableType` / `FHierarchyTableType`
- Role: Defines column/value types supported by the table runtime.

### `UHierarchyTableFactory` / `UHierarchyTableAssetDefinition`
- Role: Editor asset factory and definition for creating Hierarchy Table assets.

### `FHierarchyTableTypeHandler`
- Role: Editor handler for column types; used to create editors and validate data.

### `SHierarchyTable` / `SHierarchyTableRow`
- Role: Slate widgets that render and edit hierarchy table rows in the editor toolkit.

## 4. Typical usage patterns
- Enable the plugin and create a new Hierarchy Table asset via the content browser.
- Use the Hierarchy Table editor to add rows/columns using default type handlers or custom ones.
- Integrate runtime `FHierarchyTable` data into systems that need hierarchical lookups (e.g., animation data tables).

## 5. Version-specific notes (UE 5.7)
- Experimental flag in 5.7; no additional version-locked APIs noted.
