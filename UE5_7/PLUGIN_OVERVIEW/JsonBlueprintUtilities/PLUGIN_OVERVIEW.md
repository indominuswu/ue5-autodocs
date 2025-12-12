# Json Blueprint Utilities Plugin Overview

## 1. What this plugin does

- Adds Blueprint-accessible helpers for reading, writing, and manipulating JSON data.
- Provides custom thunk functions to map JSON fields to arbitrary struct/property types.
- Includes an uncooked-only graph module for editor-time utilities (JsonBlueprintGraph).
- Beta and disabled by default.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Blueprint nodes (`UJsonBlueprintFunctionLibrary`) let users parse/serialize JSON and map fields to structs directly in Blueprints.

## 3. Key Modules

- **JsonBlueprintUtilities** (Runtime, Default) — Blueprint function library and JSON/struct conversion helpers.
- **JsonBlueprintGraph** (UncookedOnly, Default) — Editor-time graph utilities supporting the Blueprint JSON nodes.

## 4. Important Types & APIs

### `UJsonBlueprintFunctionLibrary` (UBlueprintFunctionLibrary)

- Role: Blueprint API for JSON IO and field manipulation.
- Key functions:
  - `FromString` / `FromFile` — Parse JSON strings/files into `FJsonObjectWrapper`.
  - `ToString` / `ToFile` — Serialize a wrapper to string or file.
  - `GetField` / `SetField` (custom thunks) — Map JSON fields to arbitrary property types.
  - `StructToJsonString` — Serialize a struct to a JSON string (custom thunk).
  - `HasField`, `GetFieldNames` — Introspection helpers.

## 5. Typical usage patterns

- Enable the plugin, then use the Blueprint nodes from `UJsonBlueprintFunctionLibrary` to load/save JSON and to read/write fields into `FJsonObjectWrapper` variables.
- Use custom thunk functions to map JSON data to user-defined structs or to write struct values back into JSON.

## 6. Version-specific notes (UE 5.7)

- Marked beta in the descriptor; no additional UE 5.7-specific changes noted.

