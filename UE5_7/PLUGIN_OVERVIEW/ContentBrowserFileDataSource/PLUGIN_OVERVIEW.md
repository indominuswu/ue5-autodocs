# Content Browser - File Data Source Plugin Overview

## 1. What this plugin does

- Adds a Content Browser data source for loose files (non-asset files) so they can be browsed alongside assets.
- Disabled by default; also supported in LiveLinkHub.

## 2. Editor/Runtime surfaces

- User-facing: Yes - File data source module (EditorAndProgram, SupportedPrograms: LiveLinkHub) that lets users surface loose files alongside assets in the Content Browser.

## 3. Key Modules

- **ContentBrowserFileDataSource** (EditorAndProgram, Default)  
  - Role: Provides file-based items to the Content Browser data source framework.

## 3. Typical usage patterns

- Enable to expose loose files for browsing/selection in the Content Browser or LiveLinkHub.  
- Useful when working with external file references or pipelines that operate on loose files.

## 6. Version-specific notes (UE 5.7)

- No explicit 5.7-specific changes noted.

