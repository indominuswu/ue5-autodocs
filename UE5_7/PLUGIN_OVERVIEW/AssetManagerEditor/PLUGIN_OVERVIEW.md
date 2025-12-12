# Asset Manager Editor Plugin Overview

## 1. What this plugin does

- Adds editor UI for auditing and managing assets on disk: reference graph viewer, asset table/tree views, size map, and asset audit browser.
- Provides source-control context menu utilities and details customizations for primary asset ids/types.
- Integrates with Content Browser data source to drive asset queries and reports.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor-only asset management tools (Reference Viewer, Asset Audit, Size Map, asset tables, primary asset customizations).

## 3. Key Modules

- **AssetManagerEditor** (UncookedOnly, PreDefault)  
  - Role: Core editor tools for asset management and reference visualization.  
  - Notable areas: `AssetManagerEditorModule`, `AssetManagerEditorCommands`, `SAssetAuditBrowser`, `SSizeMap`, `AssetTable`/`SAssetTableTreeView`, `ReferenceViewer` (graph widgets/schema), source control context menu, primary asset customizations.

## 4. Important Types & APIs

- `FAssetManagerEditorModule`: Registers menus, commands, tabs, and tool windows (audit browser, size map, reference viewer, asset table).  
- `FAssetManagerEditorCommands`: Command set for toolbar/menu actions.  
- Reference Viewer: `UEdGraph_ReferenceViewer`, `UEdGraphNode_Reference`, `SReferenceViewer`, `ReferenceViewerSchema`, `ReferenceViewerSettings`, filters/history.  
- Asset table/tree: `FAssetTable`, `FAssetTreeNode`, `SAssetTableTreeView`, `FAssetDependencyGrouping`.  
- Audit/size views: `SAssetAuditBrowser`, `SSizeMap`.  
- Source control: `FAssetSourceControlContextMenu`.  
- Details customizations: `FPrimaryAssetIdCustomization`, `FPrimaryAssetTypeCustomization`.  
- Styling: `ReferenceViewerStyle`.

## 5. Typical usage patterns

- Open Asset Manager tools (Asset Audit, Reference Viewer, Size Map, Asset Table) to inspect references, dependencies, sizes, and metadata across assets.  
- Use Reference Viewer to navigate asset reference graphs with filters/history; export or analyze dependencies.  
- Use Asset Audit/Size Map to find large assets and optimize disk footprint.  
- Apply primary asset id/type customizations in details panels; use source control context menu actions from asset manager views.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific changes noted; reflects current asset management tooling in 5.7.
