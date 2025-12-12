# Asset Search Plugin Overview

## 1. What this plugin does

- Provides an editor search/indexing system for assets using SQLite-backed indexes.
- Indexes various asset types (Blueprints, levels, materials, widgets, sounds, data tables, curve tables, dialogues, generic objects) for fast text/content search.
- Adds a search browser UI with tree results and search styling; beta and disabled by default.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor-only asset search browser with indexing providers/settings for finding assets.

## 3. Key Modules

- **AssetSearch** (EditorNoCommandlet, Default, Beta)  
  - Role: Manages indexing, search database, providers, UI, and settings.  
  - Notable types: `FAssetSearchModule`, `FAssetSearchManager`, `FAssetSearchDatabase`, `FFileInfoDatabase`, `FSearchSerializer`, `IAssetIndexer`, `ISearchProvider`, `FAssetSearchCommands`, `SearchProjectSettings`/`SearchUserSettings`, UI widgets (`SSearchBrowser`, `SSearchTreeRow`, `FSearchStyle`).

## 4. Important Types & APIs

- Indexers: `FBlueprintIndexer`, `FLevelIndexer`, `FMaterialExpressionIndexer`, `FWidgetBlueprintIndexer`, `FSoundCueIndexer`, `FDataTableIndexer`, `FCurveTableIndexer`, `FDialogueWaveIndexer`, `FGenericObjectIndexer`, `FActorIndexer`.  
- Provider: `FAssetRegistrySearchProvider` queries asset registry data for indexing.  
- Databases: `FAssetSearchDatabase` and `FFileInfoDatabase` store indexed data (SQLite via `SQLiteCore`).  
- Settings: `USearchProjectSettings`, `USearchUserSettings` configure indexing/scope.  
- UI: `SSearchBrowser` main panel, `SSearchTreeRow` entries, `FSearchModel` data model, `FSearchStyle`.

## 5. Typical usage patterns

- Enable the plugin, configure project/user search settings, build the search index.  
- Use the Asset Search browser to query across indexed assets; review results in the tree and open assets directly.  
- Extend indexing by implementing `IAssetIndexer` or providers if needed.

## 6. Version-specific notes (UE 5.7)

- Beta and off by default; no explicit 5.7-specific changes noted.
