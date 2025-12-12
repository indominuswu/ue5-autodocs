# Multi-User Editing Plugin Overview

## 1. What this plugin does
- Enables collaborative multi-user editing sessions inside Unreal Editor.
- Provides runtime subsystems/Blueprint APIs for session connection, event dispatch, and replication control.
- Supplies extensive editor UI for session discovery, connection, replication stream editing, and analytics.
- Includes replication presets/assets to manage what data is synchronized between clients.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor UI for multi-user sessions plus runtime subsystem/Blueprint APIs and replication assets.

## 3. Key Modules
- **MultiUserClient** (UncookedOnly)
  - Role: Core editor app module, session browser/UX, replication control UI, and settings.
  - Notable types: replication UI controllers, transport/analytics helpers, client/session browser widgets, configuration structures.
- **MultiUserClientLibrary** (Runtime)
  - Role: Blueprint/Engine subsystem access to multi-user features.
  - Notable types: `UMultiUserSubsystem`, `UMultiUserClientStatics`, replication registration interfaces, async change actions.
- **MultiUserReplication** (Runtime)
  - Role: Replication asset types and serialization helpers.
  - Notable types: `UMultiUserReplicationStreamAsset`, `FMultiUserPropertyReplicationSelection`.
- **MultiUserReplicationEditor** (Editor)
  - Role: Asset definitions, factories, and editor UI for replication stream/preset assets.

## 4. Important Types & APIs

### `UMultiUserSubsystem`
- Role: Engine subsystem for joining/leaving sessions, enumerating clients, and sending custom events.
- Key functions: `IsConnectedToSession`, `GetLocalClientId`, `GetRemoteClientIds`, `K2_SendCustomEvent`, `RegisterCustomEventHandler`, `DispatchEvent`.
- Delegates: `OnSessionConnected`, `OnSessionDisconnected`, `OnSessionClientChanged`.

### Replication control APIs
- Interfaces: `IMultiUserReplicationRegistration`, `IMultiUserReplicationRegistrationContext` for registering discoverable replicated data.
- Async actions: `ChangeClientAsyncAction` / params for muting/authority/stream changes.
- Settings: `UMultiUserReplicationSettings`, frequency default rules.

### Asset types
- `UMultiUserReplicationStreamAsset`: Defines which properties/objects replicate in a stream.
- Preset-related types: session/client presets and stream definitions exposed via factories and asset definitions.

### Editor UX (selected highlights)
- Session browser, active session tabs, replication dashboards, authority/muting/stream views, and analytics/notification widgets.
- Preset editor toolkit (`ReplicationSessionPresetEditorToolkit`) for authoring replication presets.

## 5. Typical usage patterns
- Enable the plugin and use the Multi-User toolbar to discover and join sessions; the UI comes from the uncooked module.
- In Blueprint or editor utilities, call `UMultiUserSubsystem` to join/leave sessions, send custom events, and query clients.
- Create and edit `ReplicationStream`/preset assets via the editor asset definitions; apply them during sessions to control what replicates.
- Extend replication via `IMultiUserReplicationRegistration` implementations to expose custom data streams.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; functionality aligns with the current source tree.
