# Xcode Integration Plugin Overview

## 1. What this plugin does

- Integrates Apple Xcode as the source code accessor on macOS (including UnrealFrontend/UnrealInsights support).
- Generates/opens Xcode projects, opens files at specific lines, and adds source files.

## 2. Key Modules

- **XCodeSourceCodeAccess** (UncookedOnly, Default, Mac-only)  
  - Role: Xcode-backed `ISourceCodeAccessor` registration.  
  - Notable types: `FXCodeSourceCodeAccessor`, `FXCodeSourceCodeAccessModule`.

## 3. Important Types & APIs

### `FXCodeSourceCodeAccessor`

- Role: Implements `ISourceCodeAccessor` for Xcode.  
- Capabilities: Open solution/project, open file at line/column, add source files, save all documents, report availability.

### `FXCodeSourceCodeAccessModule`

- Role: Registers the accessor on startup for editor and supported programs.

## 4. Typical usage patterns

- Enable the plugin on macOS; choose Xcode in Editor Preferences → Source Code.  
- Use editor actions to open the project or navigate to specific source locations; Xcode is launched accordingly.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific changes noted; standard macOS Xcode integration in 5.7.
