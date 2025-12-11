# Visual Studio Integration Plugin Overview

## 1. What this plugin does

- Integrates Microsoft Visual Studio as the source code accessor on Windows (and supported programs like UnrealFrontend/UnrealInsights).
- Generates and opens solutions, jumps to files/lines, adds files to projects, and saves open documents through VS automation.
- Provides user settings for selecting the preferred VS installation/format.

## 2. Key Modules

- **VisualStudioSourceCodeAccess** (UncookedOnly, Default, Win64, supports UnrealFrontend/UnrealInsights)  
  - Role: Visual Studio-backed `ISourceCodeAccessor`, automation wrapper, settings management.  
  - Notable types: `FVisualStudioSourceCodeAccessor`, `FVisualStudioSourceCodeAccessorWrapper`, `FVisualStudioSourceCodeAccessModule`, `UVisualStudioSourceCodeAccessSettings`.

## 3. Important Types & APIs

### `FVisualStudioSourceCodeAccessor`

- Role: Core `ISourceCodeAccessor` implementation.  
- Capabilities: Detect VS installs, open solution/solution-at-path, open file at line/column, add source files, save all documents, project format selection, solution existence checks.

### `FVisualStudioSourceCodeAccessorWrapper`

- Role: Adapter used by the module to register the accessor with the source access subsystem.

### `UVisualStudioSourceCodeAccessSettings`

- Role: Editor settings object to configure preferred VS install/format.

### `FVisualStudioSourceCodeAccessModule`

- Role: Registers the accessor/wrapper and settings on startup.

## 4. Typical usage patterns

- Enable the plugin (default). In Editor Preferences → Source Code, choose Visual Studio and desired install/version.  
- Use editor actions to open the solution or navigate to specific source locations; VS is launched and focused accordingly.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific changes highlighted; integration matches the current 5.7 implementation.
