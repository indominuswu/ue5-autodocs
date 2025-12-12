# Visual Studio Code Integration Plugin Overview

## 1. What this plugin does

- Integrates Visual Studio Code as a source code accessor on Win64/Mac/Linux.
- Generates/opens workspace files, opens source files at specific lines, and adds files to projects.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Source code accessor that users select in Editor Preferences to open/jump to files in VS Code via `FVisualStudioCodeSourceCodeAccessor`.

## 3. Key Modules

- **VisualStudioCodeSourceCodeAccess** (UncookedOnly, Default)  
  - Role: VS Code-backed `ISourceCodeAccessor` and module registration.  
  - Notable types: `FVisualStudioCodeSourceCodeAccessor`, `FVisualStudioCodeSourceCodeAccessModule`.

## 4. Important Types & APIs

### `FVisualStudioCodeSourceCodeAccessor`

- Role: Implements `ISourceCodeAccessor` for VS Code.  
- Capabilities: Detect VS Code, open workspace/solution at path, open file at line/column, open/add source files, save all documents, report availability.

### `FVisualStudioCodeSourceCodeAccessModule`

- Role: Registers the accessor with the source access subsystem on startup.

## 5. Typical usage patterns

- Enable the plugin and choose VS Code in Editor Preferences > Source Code.  
- Use editor commands to open the workspace or jump to source locations; VS Code is launched with the requested file/line.

## 6. Version-specific notes (UE 5.7)

- No UE 5.7-specific changes noted; current implementation matches the 5.7 source.


