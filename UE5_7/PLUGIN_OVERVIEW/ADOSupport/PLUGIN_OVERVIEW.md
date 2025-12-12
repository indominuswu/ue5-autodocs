# ADO Support Plugin Overview

## 1. What this plugin does
- Provides ADO (ActiveX Data Objects) database connectivity from Unreal.
- Exposes a module interface to create database connection instances on demand.
- Windows-focused database access for tools or runtime where ADO is available.

## 2. Editor/Runtime surfaces
- User-facing: No - only exposes the C++ `IADOSupport` module to create `FDataBaseConnection` instances; no editor UI or Blueprint/runtime components for content teams.

## 3. Key Modules
- **ADOSupport** (Runtime)
  - Role: Module interface that can instantiate `FDataBaseConnection` objects backed by ADO.

## 4. Important Types & APIs

### `IADOSupport`
- Role: Module interface with `Get`/`IsAvailable` helpers and `CreateInstance` to obtain `FDataBaseConnection` objects.
- Usage: Load the module via `IADOSupport::Get()` and call `CreateInstance()` to open ADO connections.

## 5. Typical usage patterns
- Enable the plugin on Windows, then in code load `ADOSupport` and create database connections via `CreateInstance`.
- Use returned `FDataBaseConnection` to execute ADO queries/commands as implemented by the module.
- Suitable for tools or editor utilities needing direct database access.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
