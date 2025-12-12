# CLion Integration Plugin Overview

## 1. What this plugin does

- Integrates CLion as a source code accessor for Unreal projects on Win64/Mac/Linux.
- Detects CLion installation and opens solutions/files in the IDE.
- Provides standard source accessor features (open solution, open file at line, add files).

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor registers a CLion `ISourceCodeAccessor` so developers can open solutions/files from Unreal via Editor Preferences > Source Code.

## 3. Key Modules

- **CLionSourceCodeAccess** (UncookedOnly, Default)  
  - Role: Implements the CLion-backed `ISourceCodeAccessor` and registers it with the source code access subsystem.  
  - Notable types: `FCLionSourceCodeAccessor`, `FCLionSourceCodeAccessModule`.

## 4. Important Types & APIs

### `FCLionSourceCodeAccessor`

- Role: `ISourceCodeAccessor` implementation for CLion.  
- Key behaviors: `RefreshAvailability`/`FindExecutablePath` detect CLion; `CanAccessSourceCode`, `DoesSolutionExist`; open solution at path, open file at line, open/add source files; `SaveAllOpenDocuments`; no-op `Tick`.
- Maintains `ExecutablePath` and `bHasCLionInstalled` to decide availability.

### `FCLionSourceCodeAccessModule`

- Role: Registers the accessor on startup.

## 5. Typical usage patterns

- Enable the plugin; select CLion as the preferred source accessor in Editor Preferences (Source Code).  
- Use “Open C++ Source”/“Open Visual Studio” equivalents to launch CLion to the solution or a specific file/line.

## 6. Version-specific notes (UE 5.7)

- No UE 5.7-specific changes observed; functionality mirrors prior CLion integration.

