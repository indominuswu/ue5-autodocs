# Virtual Production Roles Plugin Overview

## 1. What this plugin does

- Manages “Virtual Production roles” (machine roles) used to configure VP systems (e.g., camera op, stage, playback).
- Provides an engine subsystem for querying/setting active roles and an editor UI for authoring available roles.
- Consumes command-line overrides (`-VPRole=Role.SubRole1|Role.SubRole2`) and propagates changes to dependent VP plugins.

## 2. Key Modules

- **VPRoles** (Runtime) – Engine subsystem that stores and queries active roles; reads roles from config and command line.
- **VPRolesEditor** (Editor) – Editor tools/settings to add/remove roles and persist them to config (VPRoles.ini).

## 3. Important Types & APIs

### `UVirtualProductionRolesSubsystem`

- Role: `UEngineSubsystem` providing access to available and active VP roles.
- Key functions: `GetActiveRoles()`, `HasActiveRole()`, `GetActiveRolesString()`, `SetActiveRoles()`, `GetAllRoles()`. Editor-only: `AddRole()`, `RemoveRole()`.
- Behavior: Tracks whether command-line roles are present/used; exposes delegates `FOnRolesChanged`/`FOnRolesChangedNative` when the role set changes; reports role sources.

### Settings (editor-only)

- `UVPRolesSettings` (config `UserVPRoles`, defined privately) persists the authored role list used by the subsystem.

## 4. Typical usage patterns

- Enable VPRoles (and VPSettings). Configure available roles in the editor (VPRolesEditor) or pass them via command line.
- Query roles at runtime using `UVirtualProductionRolesSubsystem` to branch VP behavior (e.g., enable/disable services based on role).
- In editor workflows, call `AddRole`/`RemoveRole` (or use UI) to maintain the shared role list; ensure config files are writable for source control.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
