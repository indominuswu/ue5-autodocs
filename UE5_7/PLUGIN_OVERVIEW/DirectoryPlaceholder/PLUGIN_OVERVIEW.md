# Directory Placeholder Plugin Overview

## 1. What this plugin does

- Adds a lightweight `Directory Placeholder` asset so empty folders can be committed to source control.
- Provides a content browser filter to show/hide placeholder assets.
- Includes a factory and asset definition for creating placeholders directly in the editor.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor-only placeholder asset type with content browser filter, factory, and settings.

## 3. Key Modules

- **DirectoryPlaceholder** (Editor, Default, Experimental)  
  - Role: Editor support for placeholder assets, content browser filtering, settings, and utilities.  
  - Notable types: `UDirectoryPlaceholder`, `UDirectoryPlaceholderSearchFilter`, `FDirectoryPlaceholderModule`, `UDirectoryPlaceholderFactory`, `DirectoryPlaceholderSettings`, `DirectoryPlaceholderUtils`, `UAssetDefinition_DirectoryPlaceholder`.

## 4. Important Types & APIs

### `UDirectoryPlaceholder`

- Role: Minimal `UObject` asset representing a placeholder to keep directories in source control. No properties beyond identity.

### `UDirectoryPlaceholderSearchFilter`

- Role: Content browser front-end filter extension; overrides `AddFrontEndFilterExtensions` to register a toggle for showing placeholders.

### Factories and asset integration

- `UDirectoryPlaceholderFactory`: Creates placeholder assets.  
- `UAssetDefinition_DirectoryPlaceholder`: Integrates with content browser asset actions.  
- `DirectoryPlaceholderSettings`: Plugin settings (see config) controlling visibility/behavior.  
- `DirectoryPlaceholderUtils`: Helper functions for placeholder creation and discovery.

## 5. Typical usage patterns

- Enable the plugin (experimental). Create a Directory Placeholder asset inside an otherwise empty folder to ensure the folder is tracked by source control.
- Use the content browser filter to show or hide placeholder assets while browsing.
- Configure plugin settings if needed to adjust default behavior or visibility.

## 6. Version-specific notes (UE 5.7)

- Marked experimental in the 5.7 source; no additional UE 5.7-specific changes noted.
