# Online Subsystem Steam Plugin Overview

## 1. What this plugin does

- Integrates Steam as an Online Subsystem provider for identity, friends, sessions, achievements, leaderboards, cloud, purchases, and voice.
- Handles Steam auth, encrypted app tickets, presence, lobbies/servers, and shared cloud storage through the Steamworks SDK.
- Supports Windows, macOS, and Linux targets (excluding Win64 ARM64) when Steam is enabled.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Steam OSS provider; games set `DefaultPlatformService=Steam` and use the OSS interfaces (sessions/identity/achievements/store/voice) backed by Steamworks.

## 3. Key Modules

- **OnlineSubsystemSteam** (Runtime)  
  - Role: Registers the Steam OSS provider, routes async tasks, and bridges engine online interfaces to Steamworks features.

## 4. Important Types & APIs

- `FOnlineSubsystemSteam` (subsystem)  
  - Core provider that exposes accessors for session, identity, friends, presence, cloud, leaderboards, achievements, and store.
- `FOnlineSessionSteam` (`OnlineSessionInterfaceSteam.h`, `OnlineSessionAsyncLobbySteam.h`, `OnlineSessionAsyncServerSteam.h`)  
  - Implements lobby- and server-based session flows, lobby search, invites, and session keys.
- `FOnlineIdentitySteam`, `FOnlineFriendsSteam`, `FOnlinePresenceSteam`  
  - Map Steam auth/persona data to engine identity/friends/presence APIs.
- `FOnlineAchievementsSteam`, `FOnlineLeaderboardSteam`  
  - Achievements and leaderboard read/write through Steamworks.
- `FOnlineUserCloudSteam`, `FOnlineSharedCloudSteam`, `FOnlineStoreSteam`, `FOnlinePurchaseSteam`  
  - Cloud saves and in-app purchases integration.
- `FOnlineVoiceSteam` / `FVoiceEngineSteam`  
  - Voice chat packet handling over Steam.
- `FOnlineEncryptedAppTicketInterfaceSteam`, `FOnlinePingInterfaceSteam`  
  - Utility interfaces for encrypted tickets and ping measurement.

## 5. Typical usage patterns

- Enable the plugin and set `DefaultPlatformService=Steam` (or use `-onlineplatform=Steam`) with Steamworks SDK configured.
- Use standard OnlineSubsystem interfaces (sessions, identity, achievements, leaderboards, purchases) in gameplay code/Blueprints; functionality routes to Steam.
- Configure Steam AppId and enable the `SteamShared` dependency; lobbies and invites appear in Steam overlay.
- No custom editor tools; configuration is driven via `.ini` and Steamworks setup.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview reflects the current Steam integration in the UE 5.7 source tree.

