# Online Subsystem NULL Plugin Overview

## 1. What this plugin does

- Provides a minimal “NULL” implementation of the Online Subsystem for local testing without a real platform backend.
- Implements sessions, identity, achievements, leaderboards, purchases, voice and external UI stubs that always operate locally.
- Useful for validating online game flows during development before integrating a real provider.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime Online Subsystem provider for local testing of online flows.

## 3. Key Modules

- **OnlineSubsystemNull** (Runtime)  
  - Role: Runtime Online Subsystem provider that registers as `NULL` and wires task processing.

## 4. Important Types & APIs

- `FOnlineSubsystemNull` (subsystem)  
  - Central provider registering the NULL platform; exposes accessors for session, identity, friends, achievements, leaderboards, store/purchase, external UI, and voice.
- `FOnlineSessionNull` / `FOnlineAsyncTaskManagerNull`  
  - Session handling and async task pump; supports create/find/join/destroy using in-memory data only.
- `FOnlineIdentityNull`, `FOnlineFriendsNull`, `FOnlineAchievementsNull`, `FOnlineLeaderboardNull`  
  - Lightweight in-memory identity, friends, achievements, and leaderboard implementations.
- `FOnlineExternalUINull`, `FOnlinePurchaseNull`, `FOnlineStoreV2InterfaceNull`  
  - Stubbed commerce/external UI flows that always succeed locally.
- `FOnlineVoiceImpl` (via `VoiceInterfaceNull.h`)  
  - No-op voice interface satisfying Online Subsystem contracts.

## 5. Typical usage patterns

- Enable the plugin (it is on by default) to exercise Online Subsystem APIs without a platform SDK.
- Configure `DefaultPlatformService=NULL` in `DefaultEngine.ini` to force the NULL provider.
- Use standard OnlineSubsystem interfaces (sessions, identity, friends, achievements) in gameplay code or Blueprints; behavior stays local and non-networked.
- No editor tooling or assets are added; this is purely runtime plumbing for local testing.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
