# Content Browser - Asset Data Source Plugin Overview

## 1. What this plugin does

- Supplies core asset data to the Content Browser as a data source (used by the new CB data source architecture).
- Enabled by default; also allowed in LiveLinkHub.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Default Content Browser asset data source (`ContentBrowserAssetDataSource` module, ProgramAllowList: LiveLinkHub) that populates asset items and underpins other CB data sources.

## 3. Key Modules

- **ContentBrowserAssetDataSource** (Editor, Default)  
  - Role: Provides asset data source implementation feeding the Content Browser.

## 3. Typical usage patterns

- Typically left enabled; other data source plugins (e.g., Alias, Class, File) depend on it to populate asset items.

## 6. Version-specific notes (UE 5.7)

- No explicit 5.7-specific changes noted; core data source for Content Browser.

