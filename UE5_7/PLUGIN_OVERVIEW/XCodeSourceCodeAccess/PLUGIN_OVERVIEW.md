# Xcode Integration Plugin Overview

## 1. What this plugin does

- Integrates Apple Xcode as the source code accessor on macOS (including UnrealFrontend/UnrealInsights support).
- Generates/opens Xcode projects, opens files at specific lines, and adds source files.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Source code accessor that macOS users pick in Editor Preferences to open/jump-to-line in Xcode via `FXCodeSourceCodeAccessor`.

## 3. Key Modules

- **XCodeSourceCodeAccess** (UncookedOnly, Default, Mac-only)  
  - Role: Xcode-backed `ISourceCodeAccessor` registration.  
  - Notable types: `FXCodeSourceCodeAccessor`, `FXCodeSourceCodeAccessModule`.

## 4. Important Types & APIs

### `FXCodeSourceCodeAccessor`

- Role: Implements `ISourceCodeAccessor` for Xcode.  
- Capabilities: Open solution/project, open file at line/column, add source files, save all documents, report availability.

### `FXCodeSourceCodeAccessModule`

- Role: Registers the accessor on startup for editor and supported programs.

## 5. Typical usage patterns

- Enable the plugin on macOS; choose Xcode in Editor Preferences > Source Code.  
- Use editor actions to open the project or navigate to specific source locations; Xcode is launched accordingly.

## 6. Version-specific notes (UE 5.7)

- No UE 5.7-specific changes noted; standard macOS Xcode integration in 5.7.


