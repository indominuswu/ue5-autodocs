# Perforce Source Control Plugin Overview

## 1. What this plugin does

- Integrates Perforce (P4) as a source control provider in Unreal Editor.
- Supports connection, status, changelists, check-out/submit/revert/sync/history, labeling, and settings UI.
- Enabled by default; loads early to support source control in tools and content browser.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor source control provider; users configure `FPerforceSourceControlSettings` and use the Source Control UI to check out/submit/sync Perforce changelists.

## 3. Key Modules

- **PerforceSourceControl** (UncookedOnly, EarliestPossible)  
  - Role: Full Perforce provider implementation.  
  - Notable types: `FPerforceSourceControlProvider`, `FPerforceSourceControlModule`, `FPerforceSourceControlState`, `FPerforceSourceControlRevision`, `FPerforceSourceControlOperations`, `FPerforceSourceControlSettings`, `SPerforceSourceControlSettings`, `FPerforceConnection`, `FPerforceSourceControlChangelist/State`, `IPerforceSourceControlWorker`.

## 4. Important Types & APIs

- `FPerforceSourceControlProvider`: Registers with source control subsystem; routes commands to workers; caches state; manages connections.  
- `FPerforceConnection`: Handles P4 command invocation and connection info.  
- `FPerforceSourceControlOperations`: Worker implementations for common operations (update/sync, check-out/submit/revert, history, labels, changelists, change status).  
- `FPerforceSourceControlState` / `FPerforceSourceControlRevision`: Represent file state and revisions.  
- `FPerforceSourceControlSettings` + `SPerforceSourceControlSettings`: Store and expose server/credentials/workspace settings.  
- `FPerforceSourceControlChangelist` / `FPerforceSourceControlChangelistState`: Manage changelist-based workflows.

## 5. Typical usage patterns

- Configure server/username/workspace via Perforce settings UI, then connect.  
- Use Source Control menu and content browser to check out assets, submit changelists, sync, view history/diff, and manage labels.  
- Changelist-based workflow is supported (default for UE P4).

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific changes noted; functionality matches current Perforce provider in this source tree.

