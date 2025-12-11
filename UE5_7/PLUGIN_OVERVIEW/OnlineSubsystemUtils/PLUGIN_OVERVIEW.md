# Online Subsystem Utils Plugin Overview

## 1. What this plugin does

- Provides shared runtime and Blueprint utilities for Online Subsystem implementations.
- Adds beacon framework for lightweight client/host connections (party and spectator beacons) and voice helpers.
- Supplies Blueprint nodes for in-app purchases, leaderboards, and other online flows.

## 2. Key Modules

- **OnlineSubsystemUtils** (Runtime)  
  - Role: Core runtime helpers (beacons, voice packet handling, Online Account storage, base utilities).
- **OnlineBlueprintSupport** (UncookedOnly)  
  - Role: Blueprint nodes/K2 graph support for online features (in-app purchases, leaderboards).

## 3. Important Types & APIs

- `AOnlineBeacon`, `AOnlineBeaconHost`, `AOnlineBeaconClient`, `AOnlineBeaconHostObject`  
  - Base actors enabling lightweight TCP beacons for out-of-band signaling.
- `APartyBeaconHost`, `APartyBeaconClient`, `FPartyReservation`, `ASpectatorBeaconHost`, `ASpectatorBeaconClient`  
  - Reservation systems for parties and spectators, including state replication.
- `UVoipListenerSynthComponent`, `FOnlineVoiceImpl`, `FVoicePacketImpl`  
  - Voice capture/playback support and packet handling for Online Subsystem voice channels.
- `UOnlineSubsystemUtils` (module utilities)  
  - Helper functions to access subsystems and create unique net ids.
- Blueprint nodes (`K2Node_InAppPurchase*`, `K2Node_Leaderboard*`)  
  - K2 nodes that wrap in-app purchase, receipt querying, and leaderboard flush/query flows.

## 4. Typical usage patterns

- Enable alongside a concrete Online Subsystem (e.g., Steam, EOS) to use beacon-based matchmaking/lobbies or reservation systems.
- In code, derive from `AOnlineBeaconHostObject`/`AOnlineBeaconClient` for custom signaling channels; use party/spectator beacons for lobby and spectator features.
- Use Blueprint nodes for purchasing and leaderboard operations without writing C++ wrappers.
- Configure voice options in Online Subsystem settings; `UVoipListenerSynthComponent` can be attached to actors to monitor incoming voice.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview reflects the current utilities in the UE 5.7 source tree.
