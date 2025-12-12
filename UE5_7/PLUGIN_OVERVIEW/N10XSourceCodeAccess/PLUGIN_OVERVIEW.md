# 10X Editor Integration Plugin Overview

## 1. What this plugin does

- Integrates the 10X Editor as a source code accessor on Win64.
- Allows Unreal to open solutions/projects and jump to files/lines in 10X.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor users pick 10X as their source accessor in Editor Preferences, then use it to open projects/files and navigate to lines directly from Unreal.

## 3. Key Modules

- **N10XSourceCodeAccess** (UncookedOnly, Default, Win64-only)  
  - Role: Implements and registers a 10X-backed `ISourceCodeAccessor`.  
  - Notable types: `FN10XSourceCodeAccessor`, `FN10XSourceCodeAccessModule`.

## 4. Important Types & APIs

### `FN10XSourceCodeAccessor`

- Role: `ISourceCodeAccessor` implementation for 10X Editor.  
- Capabilities: Check availability, open solution/solution-at-path, open file at line, add source files, save all documents; manages executable path detection internally.

### `FN10XSourceCodeAccessModule`

- Role: Registers the accessor on startup.

## 5. Typical usage patterns

- Enable the plugin on Win64; select 10X as the source accessor in Editor Preferences.  
- Use editor commands to open the project or navigate to specific source locations in 10X.

## 6. Version-specific notes (UE 5.7)

- No UE 5.7-specific changes noted; standard 10X integration as shipped in 5.7.

