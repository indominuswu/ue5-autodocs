# Online Subsystem Tencent Plugin Overview

## 1. What this plugin does

- Provides a Tencent/Rail Online Subsystem provider for identity, friends, presence, sessions, purchases, store, and messaging.
- Bridges engine online interfaces to the Tencent Rail SDK on Windows and Linux targets.
- Includes platform-specific async task handling, message sanitization, and playtime limit support.

## 2. Key Modules

- **OnlineSubsystemTencent** (Runtime)  
  - Role: Registers the Tencent provider, owns async task processing, and exposes Rail-backed online interfaces.

## 3. Important Types & APIs

- `FOnlineSubsystemTencent` (subsystem)  
  - Core provider exposing accessors for session, identity, friends, presence, external UI, store/purchase, and message sanitizer; manages Rail SDK initialization.
- `FOnlineSessionTencent` / `FOnlineSessionTencentRail`  
  - Session management over Rail (create/find/join/destroy, invites).
- `FOnlineIdentityTencent`, `FOnlineFriendsTencent`, `FOnlinePresenceTencent`  
  - Identity, friends list, and presence mapping to Rail accounts.
- `FOnlinePurchaseTencent`, `FOnlineStoreTencent`, `FOnlineExternalUITencent`  
  - Commerce and UI flows against Rail services.
- `FOnlineMessageSanitizerTencent`, `FOnlineUserTencent`, `FOnlinePlayTimeLimit`  
  - Content filtering and playtime limit helpers specific to Tencent requirements.
- `FRailSdkWrapper`, `FTencentDllMgr`  
  - Helper classes that load and mediate access to the Rail SDK binaries.

## 4. Typical usage patterns

- Enable the plugin and set `DefaultPlatformService=Tencent` for Windows/Linux builds targeting Rail.
- Provide Rail SDK binaries/configuration; use standard OnlineSubsystem APIs (sessions, identity, friends, purchases) from game code/Blueprints.
- No editor UI is added; configuration is `.ini` driven and handled through the Rail SDK setup.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current Tencent integration in the UE 5.7 source tree.
