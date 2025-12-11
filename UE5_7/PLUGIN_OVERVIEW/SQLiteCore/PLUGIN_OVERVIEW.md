# SQLite Plugin Overview

## 1. What this plugin does
- Wraps the SQLite C library with lightweight C++ helpers for database access.
- Provides prepared statement and type helpers for executing SQL against SQLite files.
- Intended for use by engine programs and services (multi-user servers, LiveLinkHub, recovery service).

## 2. Key Modules
- **SQLiteCore** (Runtime)
  - Role: Core SQLite wrapper API available early in startup (PreDefault).
  - Notable types: `FSQLiteDatabase`, `FSQLitePreparedStatement`, `ESQLiteDatabaseOpenMode`, `ESQLitePreparedStatementFlags`.

## 3. Important Types & APIs
- `FSQLiteDatabase`
  - Role: RAII wrapper around an SQLite database handle.
  - Key functions: open/close database, execute SQL, bind parameters, transaction helpers (via prepared statements).
- `FSQLitePreparedStatement`
  - Role: Prepared statement wrapper supporting binding/querying values and iteration of result rows.
- `ESQLiteDatabaseOpenMode`, `ESQLitePreparedStatementFlags`
  - Role: Enumerations configuring open modes and statement behavior.

## 4. Typical usage patterns
- Enable the plugin in programs or tools that need SQLite access.
- Create an `FSQLiteDatabase`, open a file (read-only/read-write/create), then prepare statements (`FSQLitePreparedStatement`) to run queries safely.
- Use type-safe bind/column accessors when stepping through results.
- Pair with `SQLiteSupport` when integrating with the engine’s `FDataBaseConnection` interface.

## 5. Version-specific notes (UE 5.7)
- References SQLite_v3.47.1 license in ThirdParty; no additional UE 5.7-specific notes found.
