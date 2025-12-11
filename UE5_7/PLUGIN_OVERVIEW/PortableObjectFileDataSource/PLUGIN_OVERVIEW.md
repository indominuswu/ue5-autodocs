# Portable Object File Data Source Plugin Overview

## 1. What this plugin does
- Adds portable object (.po) file support as a Content Browser data source.
- Allows browsing, importing, or referencing PO localization files directly inside the editor.
- Extends Content Browser file data sources specifically for localization assets.

## 2. Key Modules
- **PortableObjectFileDataSource** (Editor)  
  - Role: Registers the PO data source with the Content Browser file data source framework.  
  - Notable types: `IPortableObjectFileDataSourceModule`.

## 3. Important Types & APIs
### `IPortableObjectFileDataSourceModule`
- Role: Module interface used to register/unregister the PO data source.
- Key functions: startup/shutdown module hooks, data source registration with the Content Browser’s file data source system.

## 4. Typical usage patterns
- Enable the plugin (depends on `ContentBrowserFileDataSource`) to surface `.po` files as browseable items in the Content Browser.
- Use standard Content Browser interactions (open, view, import) on PO files once the data source is registered.

## 5. Version-specific notes (UE 5.7)
- No UE 5.7-specific notes; plugin is stable and editor-only in this source tree.
