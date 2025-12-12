# Portable Object File Data Source Plugin Overview

## 1. What this plugin does
- Adds portable object (.po) file support as a Content Browser data source.
- Allows browsing, importing, or referencing PO localization files directly inside the editor.
- Extends Content Browser file data sources specifically for localization assets.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor Content Browser data source that surfaces `.po` localization files for browsing/importing.

## 3. Key Modules
- **PortableObjectFileDataSource** (Editor)  
  - Role: Registers the PO data source with the Content Browser file data source framework.  
  - Notable types: `IPortableObjectFileDataSourceModule`.

## 4. Important Types & APIs
### `IPortableObjectFileDataSourceModule`
- Role: Module interface used to register/unregister the PO data source.
- Key functions: startup/shutdown module hooks, data source registration with the Content Browser’s file data source system.

## 5. Typical usage patterns
- Enable the plugin (depends on `ContentBrowserFileDataSource`) to surface `.po` files as browseable items in the Content Browser.
- Use standard Content Browser interactions (open, view, import) on PO files once the data source is registered.

## 6. Version-specific notes (UE 5.7)
- No UE 5.7-specific notes; plugin is stable and editor-only in this source tree.

