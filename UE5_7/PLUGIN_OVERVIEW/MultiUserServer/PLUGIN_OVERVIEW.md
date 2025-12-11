# Multi User Server Plugin Overview

## 1. What this plugin does
- Provides the standalone Multi-User Server application UI and logic for hosting collaborative editing sessions.
- Visualizes connected clients, sessions, transport logs, package transmissions, and session history.
- Exposes console commands and server preferences for managing sessions.

## 2. Key Modules
- **MultiUserServer** (UncookedOnly)
  - Role: Server app module, window/tabs/widgets, console commands, and server-side settings.
  - Notable types: `IMultiUserServerModule`, server window/tab controllers, transport log/clients/package viewer widgets, `MultiUserServerUserPreferences`, `MultiUserServerPackageTransmissionSettings`, `ConcertTransportLogSettings`.

## 3. Important Types & APIs

### `IMultiUserServerModule`
- Role: Module interface to start/stop the server UI and expose server-specific functionality.

### Server UI components (selected)
- Controllers for server window/tabs (`ConcertServerWindowController`, `ConcertServerTabs`), session browsers, client network stats, package transmission tables, transport log views, and status bars.
- Filtering utilities for log/package views and network graphs.

### Settings
- `MultiUserServerUserPreferences`, `MultiUserServerPackageTransmissionSettings`, `MultiUserServerColumnVisibilitySettings`, `ConcertTransportLogSettings` configure UI layout, logging, and transfer display.

### Console/utility classes
- `ConcertConsoleCommandExecutor`, server console variables for enabling/disabling features or logging.

## 4. Typical usage patterns
- Run the Multi-User Server app (with the plugin enabled) to host sessions used by Multi-User clients.
- Use the server UI to monitor clients, inspect package transmission, review transport logs, and manage archived/live sessions.
- Adjust server preferences and logging options via the provided settings classes or console commands.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview reflects the current plugin contents.
