# KDevelop Integration Plugin Overview

## 1. What this plugin does

- Integrates KDevelop as a source code accessor on Linux.
- Lets the editor open the generated project and jump to files/lines inside KDevelop.

## 2. Key Modules

- **KDevelopSourceCodeAccess** (UncookedOnly, Default, Linux-only)  
  - Role: KDevelop-backed `ISourceCodeAccessor` registration.  
  - Notable types: `FKDevelopSourceCodeAccessor`, `FKDevelopSourceCodeAccessModule`.

## 3. Important Types & APIs

### `FKDevelopSourceCodeAccessor`

- Role: Implements `ISourceCodeAccessor` for KDevelop.  
- Capabilities: Determine availability, open solution, open file at line, add source files, save documents; no special tick behavior.

### `FKDevelopSourceCodeAccessModule`

- Role: Registers the accessor during module startup.

## 4. Typical usage patterns

- Enable the plugin on Linux and choose KDevelop in Editor Preferences → Source Code.  
- Use editor actions to open the project or specific source locations in KDevelop.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific changes noted; standard KDevelop integration in 5.7.
