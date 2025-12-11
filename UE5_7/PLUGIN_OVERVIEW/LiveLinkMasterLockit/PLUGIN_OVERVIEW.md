# LiveLinkMasterLockit Plugin Overview

## 1. What this plugin does
- Integrates with Ambient MasterLockit metadata servers to stream metadata/timecode as LiveLink subjects.
- Provides a LiveLink source factory and editor UI for configuring MasterLockit connections.

## 2. Key Modules
- **LiveLinkMasterLockit** (Runtime)  
  - Role: Implements the MasterLockit LiveLink source.
  - Notable types: `ULiveLinkMasterLockitSourceFactory`, `ULiveLinkMasterLockitConnectionSettings`, `ULiveLinkMasterLockitSourceSettings`.
- **LiveLinkMasterLockitEditor** (Editor)  
  - Role: UI panel for source creation.
  - Notable types: `SLiveLinkMasterLockitSourcePanel`.

## 3. Important Types & APIs

### `ULiveLinkMasterLockitSourceFactory`
- Role: LiveLink source factory that builds a creation panel (delegated to `SLiveLinkMasterLockitSourcePanel`) and constructs sources from serialized connection strings.
- Static helper: `CreateConnectionString` builds the connection string from settings.

### Connection/settings types
- `FLiveLinkMasterLockitConnectionSettings` and source settings classes carry network/subject configuration for the MasterLockit stream.

## 4. Typical usage patterns
- LiveLink panel: Add a MasterLockit source, configure server settings in the creation panel, and start streaming metadata/timecode into LiveLink.
- Runtime/editor: Consume the resulting subjects to drive cameras or log slate/timecode metadata during virtual production shoots.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; plugin is typically disabled until needed in virtual production setups.

