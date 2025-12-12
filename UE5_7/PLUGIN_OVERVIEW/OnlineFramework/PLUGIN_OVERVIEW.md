# Online Framework Plugin Overview

## 1. What this plugin does
- Provides shared gameplay-facing online systems: QoS probing, party/lobby beacons, social/chat, patch/hotfix, rejoin, and login flow UI.
- Supplies runtime modules that layer on OnlineSubsystem/OnlineServices for gameplay features.
- Includes playtime limit tracking and platform-aware login flows.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Exposes gameplay-facing online features (QoS beacons, lobby/party/social systems, `UOnlineHotfixManager`/`UUpdateManager`, LoginFlow UI) that games integrate directly.

## 3. Key Modules
- **Qos** (Runtime): Region/QoS probing via beacon hosts/clients and latency stats.
- **Party** (Runtime): Social graph, party membership, chat channels, and replication support.
- **Lobby** (Runtime): Lobby beacon host/client/state for pre-session gathering.
- **PatchCheck** (Runtime): Patch version checking helpers before launching online play.
- **Hotfix** (Runtime): `UUpdateManager` and `UOnlineHotfixManager` for live hotfix delivery.
- **Rejoin** (Runtime): Rejoin checks and workflows after disconnects.
- **PlayTimeLimit** (Runtime): User-level playtime tracking and restrictions.
- **LoginFlow** (ClientOnly): Platform login flow UI/views (Win/Linux), excluded on Mac.

## 4. Important Types & APIs
### `QosBeaconClient` / `QosBeaconHost` / `QosEvaluator` / `QosRegionManager`
- Role: Beacon-based latency measurement and region selection.
- Key properties: region definitions, measurement stats, thresholds, and evaluation routines.
### `LobbyBeaconClient`, `LobbyBeaconHost`, `LobbyBeaconState`, `LobbyBeaconPlayerState`
- Role: Lightweight lobby replication and handoff before session travel.
### Party & Social classes (`SocialToolkit`, `SocialManager`, `SocialUser`, `SocialParty`, `Chatroom`, `SocialChatManager`)
- Role: Runtime social graph, party membership, chat channels, and slash-command handling.
### `UOnlineHotfixManager` / `UUpdateManager`
- Role: Pull and apply hotfix manifests; manage patch/update state machine.
### `PlayTimeLimitImpl` / `PlayTimeLimitUser`
- Role: Track and enforce per-user playtime budgets.

## 5. Typical usage patterns
- Enable alongside OnlineSubsystem/OnlineServices; configure QoS regions and call QoS evaluation before matchmaking.
- Host/join `LobbyBeaconHost`/`LobbyBeaconClient` actors to manage lobby membership and transfer to game sessions.
- Use social classes to maintain friend/party state, chat channels, and party interactions in UI.
- Integrate `UOnlineHotfixManager` in game instance for live updates; use `UUpdateManager` for patch flow.
- Invoke LoginFlow UI for platform authentication on supported platforms.

## 6. Version-specific notes (UE 5.7)
- No explicit 5.7-only notes; modules align with current OSS/Services stack. LoginFlow is denied on Mac per plugin metadata.

