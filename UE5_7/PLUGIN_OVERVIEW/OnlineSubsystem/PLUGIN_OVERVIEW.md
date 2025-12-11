# Online Subsystem Plugin Overview

## 1. What this plugin does
- Defines the legacy Online Subsystem (OSSv1) interfaces and base runtime implementation.
- Provides delegates, async task management, notifications, and typed feature interfaces (sessions, identity, friends, achievements, purchases, etc.).
- Serves as the foundation for platform-specific OSS plugins.

## 2. Key Modules
- **OnlineSubsystem** (Runtime): Core OSS interfaces, async task manager, and module management.

## 3. Important Types & APIs
### Core classes (`IOnlineSubsystem`, `FOnlineSubsystemImpl`, `FOnlineSubsystemModule`)
- Role: Subsystem lifecycle, factory/registration, and access to feature interfaces.
### Async and serialization (`FOnlineAsyncTaskManager`, `FNboSerializeToBuffer`, `FNboSerializeFromBuffer`, `FOnlineJsonSerializer`)
- Role: Manage async operations and network-safe serialization.
### Feature interfaces (`IOnlineSession`, `IOnlineIdentity`, `IOnlineFriends`, `IOnlineLeaderboards`, `IOnlinePurchase`, `IOnlineAchievements`, `IOnlineStats`, `IOnlineChat`, `IOnlineParty`, `IOnlineTurnBased`, `IOnlineGameActivity`, `IOnlineTournament`, `IOnlineUserCloud`, `IOnlineSharedCloud`, `IOnlineStoreV2`, `IOnlineMessage`, `IOnlineEntitlements`, `IOnlineGroups`, etc.)
- Role: Contracts for platform implementations across online capabilities.
### Utility types (`OnlineSessionSettings`, `OnlineSubsystemNames`, `OnlineSubsystemTypes`, `OnlineError`)
- Role: Common data structures for session configuration, identifiers, and error handling.

## 4. Typical usage patterns
- Enable as the base online module; select a platform OSS plugin (e.g., IOS, GooglePlay, EOS) via configuration.
- Access feature interfaces through `IOnlineSubsystem::Get()` to create/join sessions, handle identity/auth, friends, leaderboards, purchases, chat, etc.
- Implement new OSS providers by deriving from the feature interfaces and registering with the module.

## 5. Version-specific notes (UE 5.7)
- No explicit 5.7-specific notes; represents the current OSSv1 baseline shipped with UE 5.7.
