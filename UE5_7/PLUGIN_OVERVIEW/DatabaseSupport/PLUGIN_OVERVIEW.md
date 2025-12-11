# Database Support Plugin Overview

## 1. What this plugin does

- Provides abstract database interfaces used by platform-specific database connectors.
- Defines core types for record sets, column metadata, and query construction without bundling an actual driver.
- Disabled by default; intended to be paired with platform/database-specific implementations.

## 2. Key Modules

- **DatabaseSupport** (Runtime)  
  - Role: Base database abstractions and helper enums shared by database plugins.
  - Notable types: `FDataBaseRecordSet`, `FDatabaseColumnInfo`, `EDataBaseUnrealTypes`.

## 3. Important Types & APIs

### `FDataBaseRecordSet`
- Role: Base iterator interface for database query results.
- Key functions: `MoveToFirst`, `MoveToNext`, `IsAtEnd`, `GetRecordCount`, and typed getters for column values.

### `FDatabaseColumnInfo`
- Role: Describes a column’s name and data type in a result set.
- Key properties: `ColumnName`, `DataType` (`EDataBaseUnrealTypes` covering float/int/string).

### `EDataBaseUnrealTypes`
- Role: Enumerates the supported data types exposed by the abstraction layer.

## 4. Typical usage patterns

- Enable alongside a platform-specific database plugin; use the shared types to implement or consume database queries.
- Iterate over `FDataBaseRecordSet` in custom code to fetch column values using the metadata in `FDatabaseColumnInfo`.
- The plugin itself does not expose Blueprint utilities; it provides C++ interfaces for other modules.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific behaviors noted; plugin serves as an abstract layer in this branch.
