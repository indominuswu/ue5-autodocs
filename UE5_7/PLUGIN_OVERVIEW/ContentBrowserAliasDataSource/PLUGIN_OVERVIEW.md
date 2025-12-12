# Content Browser - Alias Data Source Plugin Overview

## 1. What this plugin does

- Adds a Content Browser data source that lets items appear in alias locations in addition to their original paths.
- Useful for organizing or surfacing assets in multiple virtual folders without moving them on disk.
- Beta and disabled by default.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor Content Browser data source users enable to mirror assets into alias virtual folders without moving them on disk (depends on `ContentBrowserAssetDataSource`).

## 3. Key Modules

- **ContentBrowserAliasDataSource** (Editor, Default)  
  - Role: Implements alias data source behavior for the Content Browser.  
  - Dependencies: Requires `ContentBrowserAssetDataSource`.

## 3. Typical usage patterns

- Enable the plugin to allow alias mappings so assets can be browsed under alternate virtual directories.  
- Configure alias rules (via associated settings/UI) to control where items are mirrored.

## 6. Version-specific notes (UE 5.7)

- Beta, off by default; no explicit 5.7-specific changes noted.

