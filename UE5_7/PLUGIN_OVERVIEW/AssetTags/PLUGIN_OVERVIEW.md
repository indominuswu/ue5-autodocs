# Asset Tags Plugin Overview

## 1. What this plugin does
- Provides high-level management and access to asset tags and collections for runtime and editor scripting.
- Exposes an engine subsystem with Blueprint-callable functions for creating, modifying, and querying collections.
- Enabled by default for general asset tagging workflows.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Blueprint-accessible asset tag subsystem for runtime/editor utilities managing collections.

## 3. Key Modules
- **AssetTags** (Runtime, Default)
  - Role: Engine subsystem and supporting APIs for asset tag/collection management.

## 4. Important Types & APIs
- `UAssetTagsSubsystem` (EngineSubsystem)
  - Role: Blueprint-accessible API for creating/destroying/renaming collections and adding/removing assets.
  - Key functions: `CreateCollection`, `DestroyCollection`, `RenameCollection`, `EmptyCollection`, `AddAssetToCollection` variants, `RemoveAssetFromCollection` variants, plus SoftObjectPath-based helpers.
  - Notes: Many functions are marked deprecated in 5.6 in favor of the Collection Manager Scripting Subsystem; soft object path usage preferred over full path names.

## 5. Typical usage patterns
- Access the subsystem via Blueprint (`Get Asset Tags Subsystem`) or C++ to manage collections at runtime or in editor utilities.
- Use SoftObjectPath-based functions to add/remove assets from collections; avoid deprecated full-path overloads.
- For new projects, consider the Collection Manager Scripting Subsystem for future-proofing while still leveraging this plugin where needed.

## 6. Version-specific notes (UE 5.7)
- Several subsystem methods are marked deprecated in 5.6 with guidance to use the Collection Manager Scripting Subsystem; this carries into UE 5.7.
