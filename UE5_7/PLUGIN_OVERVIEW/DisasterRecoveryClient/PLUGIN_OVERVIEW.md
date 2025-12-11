# Recovery Hub (DisasterRecoveryClient) Plugin Overview

## 1. What this plugin does

- Tracks editor changes to support recovery in the event of a crash.
- Integrates with Concert services to record session state and offer restore options.
- Provides an editor UI (“Recovery Hub”) for reviewing and applying recovery tasks.

## 2. Key Modules

- **DisasterRecoveryClient** (EditorNoCommandlet) – Editor-only module that records changes, manages recovery sessions, and exposes UI.

## 3. Important Types & APIs

- `FDisasterRecoverySessionManager` / `FDisasterRecoverySessionInfo` – Manage recovery sessions, including captured checkpoints and metadata.
- `UDisasterRecoverySettings` – Editor settings controlling whether recovery is enabled and how data is captured.
- `FDisasterRecoveryTasks` – Defines the recovery tasks run when restoring a session.
- `FDisasterRecoveryUtil` – Helper functions for recovery data handling.
- `SDisasterRecoveryHub` – Slate UI for the Recovery Hub where users trigger restore operations.

## 4. Typical usage patterns

- Enable the plugin in editor builds to automatically record recovery data while working.
- Configure `UDisasterRecoverySettings` to control capture frequency and storage locations.
- If the editor exits unexpectedly, launch the Recovery Hub UI to inspect available recovery sessions and apply the desired restore tasks.
- For teams using Concert, sessions can integrate with shared Concert infrastructure to store and retrieve recovery data.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
