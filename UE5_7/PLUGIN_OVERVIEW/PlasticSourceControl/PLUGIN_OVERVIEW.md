# Plastic SCM (Unity Version Control) Plugin Overview

## 1. What this plugin does

- Integrates Unity Version Control (Plastic SCM) as a source control provider (Win64/Linux).
- Supports changelists/branches/changesets/locks workflows with rich UI panels.
- Provides status/diff/submit/sync/history operations plus project settings and menu extensions.

## 2. Key Modules

- **PlasticSourceControl** (UncookedOnly, EarliestPossible, Win64/Linux)  
  - Role: Full Plastic SCM provider implementation with UI.  
  - Notable types: `FPlasticSourceControlProvider`, `FPlasticSourceControlModule`, `FPlasticSourceControlState`, `FPlasticSourceControlRevision`, `FPlasticSourceControlOperations`, `FPlasticSourceControlChangelist/State`, `FPlasticSourceControlBranchesWindow`, `FPlasticSourceControlChangesetsWindow`, `FPlasticSourceControlLocksWindow`, `FPlasticSourceControlMenu`, `FPlasticSourceControlSettings`/`ProjectSettings`, `FPlasticSourceControlUtils`, `FPlasticSourceControlParsers`, `FPlasticSourceControlShell`, `IPlasticSourceControlWorker`.

## 3. Important Types & APIs

- Provider/core: `FPlasticSourceControlProvider` registers with source control subsystem; routes commands to workers; manages connection/session state.  
- Operations/workers: `FPlasticSourceControlOperations` implements checkout/submit/revert/sync/history/lock/branch operations; `IPlasticSourceControlWorker` interface.  
- State/revision: `FPlasticSourceControlState` and `FPlasticSourceControlRevision` represent file status and historical revisions.  
- UI: Slate widgets for branches (`SPlasticSourceControlBranchesWidget`/`Row`), changesets (`SPlasticSourceControlChangesetsWidget`/`Row`/`FileRow`), locks (`SPlasticSourceControlLocksWidget`/`Row`), create/rename/delete branch dialogs, status bar, settings panel (`SPlasticSourceControlSettings`), console/log, menu extensions.  
- Utilities: `FPlasticSourceControlUtils`, `FPlasticSourceControlParsers`, `ScopedTempFile`, `PackageUtils`, `Notification` helpers; shell helpers for invoking cm/semantic parsing.  
- Project settings: `FPlasticSourceControlProjectSettings` and user settings for server/workspace credentials.

## 4. Typical usage patterns

- Configure server/workspace credentials in Plastic settings; connect via Source Control menu.  
- Use changelist/branch-aware workflows: view and manage branches/changesets/locks, check out/submit, sync, diff, and view history.  
- Use UI panels to manage branches and locks, and the status bar/menu for quick actions.

## 5. Version-specific notes (UE 5.7)

- Plugin is not marked Beta; Win64/Linux allow list. No explicit UE 5.7-only changes noted; overview reflects current 5.7 source.
