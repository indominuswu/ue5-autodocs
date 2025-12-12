# SQLite Support Plugin Overview

## 1. What this plugin does
- Bridges the core SQLite wrapper into the engine database abstraction (`FDataBaseConnection`).
- Provides result set helpers so existing database clients can consume SQLite query results.
- Depends on `DatabaseSupport` and `SQLiteCore`.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Provides `FSQLiteDatabaseConnection`/`FSQLiteResultSet` implementations of the engine DB interfaces for projects that want SQLite via `FDataBaseConnection`.

## 3. Key Modules
- **SQLiteSupport** (Runtime)
  - Role: Implements database connection and record set classes backed by SQLite.
  - Notable types: `FSQLiteDatabaseConnection`, `FSQLiteResultSet`.

## 4. Important Types & APIs
- `FSQLiteDatabaseConnection` (extends `FDataBaseConnection`)
  - Role: Opens/closes SQLite files and executes commands, returning SQLite-specific result sets.
  - Key functions: `Open`, `Close`, `Execute` (command-only or returning `FSQLiteResultSet`), `GetLastError`.
- `FSQLiteResultSet` (extends `FDataBaseRecordSet`)
  - Role: Iterates over rows returned by SQLite queries, exposing column accessors to callers.

## 5. Typical usage patterns
- Enable alongside `SQLiteCore` to use SQLite through the engine’s database interfaces.
- Construct `FSQLiteDatabaseConnection`, call `Open` with a file path, and run SQL using `Execute`.
- Use the `FSQLiteResultSet` returned by `Execute` when selecting data; free the record set after consumption per API contract.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

