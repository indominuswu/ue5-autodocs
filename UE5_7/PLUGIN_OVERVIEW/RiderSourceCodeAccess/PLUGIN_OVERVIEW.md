# Rider Integration Plugin Overview

## 1. What this plugin does

- Integrates JetBrains Rider as a source code accessor on Win64/Mac/Linux.
- Locates Rider installations per-platform, generates/opens solutions, and launches files at specific lines.
- Provides UI styling/assets for editor integration.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Source code accessor users select in Editor Preferences, enabling open/jump-to-line workflows in Rider via `FRiderSourceCodeAccessor`.

## 3. Key Modules

- **RiderSourceCodeAccess** (EditorNoCommandlet, Default)  
  - Role: Rider-backed `ISourceCodeAccessor`, path discovery, and style registration.  
  - Notable types: `FRiderSourceCodeAccessor`, `FRiderSourceCodeAccessModule`, `FRiderPathLocator` (Common/Linux/Mac/Win variants), `FRiderSourceCodeAccessStyleSet`.

## 4. Important Types & APIs

### `FRiderSourceCodeAccessor`

- Role: Implements `ISourceCodeAccessor` for Rider.  
- Capabilities: Detect Rider via `FRiderPathLocator`, open solution/solution-at-path, open file at line/column, open/add source files, save all documents, report availability.

### `FRiderPathLocator` (+ platform impls)

- Role: Finds Rider executable on each platform (Win/Mac/Linux implementations).  
- Shared logic in `Common` plus per-platform overrides.

### `FRiderSourceCodeAccessStyleSet`

- Role: Registers Slate style resources used by the integration UI.

### `FRiderSourceCodeAccessModule`

- Role: Registers accessor and styles on startup; cleans up on shutdown.

## 5. Typical usage patterns

- Enable the plugin; select Rider in Editor Preferences > Source Code.  
- Use editor commands to open the solution or jump to source locations; Rider will be launched via the discovered executable.

## 6. Version-specific notes (UE 5.7)

- No UE 5.7-specific changes flagged; plugin reflects current Rider integration shipped with 5.7.


