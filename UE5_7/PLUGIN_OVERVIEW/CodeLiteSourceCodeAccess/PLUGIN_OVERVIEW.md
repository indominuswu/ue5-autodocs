# CodeLite Integration Plugin Overview

## 1. What this plugin does

- Integrates CodeLite as a source code accessor on Linux.
- Supports opening the generated project/solution and specific source files from the editor.
- Beta-marked integration; focuses on IDE launching rather than in-IDE automation.

## 2. Key Modules

- **CodeLiteSourceCodeAccess** (UncookedOnly, Default, Linux-only, Beta)  
  - Role: Provides a CodeLite-backed `ISourceCodeAccessor` and registers it with the source code access subsystem.  
  - Notable types: `FCodeLiteSourceCodeAccessor`, `FCodeLiteSourceCodeAccessModule`.

## 3. Important Types & APIs

### `FCodeLiteSourceCodeAccessor`

- Role: Implements `ISourceCodeAccessor` for CodeLite.  
- Capabilities: Detects/launches CodeLite, opens solution or files at specific lines, adds source files, saves open documents, reports availability.

### `FCodeLiteSourceCodeAccessModule`

- Role: Registers the accessor during module startup.

## 4. Typical usage patterns

- Enable the plugin on Linux, set CodeLite as the preferred source accessor in Editor Preferences.  
- Use editor commands to open the solution or jump to a file/line in CodeLite.

## 5. Version-specific notes (UE 5.7)

- Marked Beta; no UE 5.7-specific behavior called out beyond current integration state.
