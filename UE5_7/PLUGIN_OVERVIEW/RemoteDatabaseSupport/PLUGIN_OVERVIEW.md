# Remote Database Support Plugin Overview

## 1. What this plugin does
- Provides a database connection implementation that proxies DB access over a socket to a remote database service.
- Allows platforms without native DB drivers to execute SQL through the proxy.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Runtime database API (`FRemoteDatabaseConnection`/`FRemoteDataBaseRecordSet`) that developers use to run SQL via a remote proxy when local drivers are unavailable.

## 3. Key Modules
- **RemoteDatabaseSupport** (Runtime)  
  - Exposes `FRemoteDatabaseConnection` and associated record set implementation; module interface `IRemoteDatabaseSupport`.

## 4. Important Types & APIs
### `FRemoteDatabaseConnection` (extends `FDataBaseConnection`)
- Role: Opens a socket to a remote DB proxy and forwards commands.
- Key functions: `Open(ConnectionString, RemoteConnectionIP, RemoteConnectionStringOverride)`, `Close()`, `Execute(CommandString)`, `Execute(CommandString, RecordSet&)`, `SetConnectionString`.

### `FRemoteDataBaseRecordSet` (extends `FDataBaseRecordSet`)
- Role: Represents result sets retrieved via the proxy.
- Key functions: cursor movement (`MoveToFirst`, `MoveToNext`, `IsAtEnd`) and value accessors (`GetString`, `GetInt`, `GetFloat`).

### `IRemoteDatabaseSupport`
- Role: Module interface helper with `Get()` / `IsAvailable()` for loading the module.

## 5. Typical usage patterns
- Enable the plugin on targets that need DB access but lack direct driver support.
- Instantiate `FRemoteDatabaseConnection`, call `Open` with the proxy IP and connection string override, then execute SQL commands as usual.
- Iterate results through `FRemoteDataBaseRecordSet` returned from `Execute`.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

