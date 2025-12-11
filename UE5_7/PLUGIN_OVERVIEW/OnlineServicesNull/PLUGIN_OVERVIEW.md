# Online Services Null Plugin Overview

## 1. What this plugin does
- Implements an Online Services provider with no external backend (local/null implementation).
- Useful for local testing of OSSv2 flows without third-party services.

## 2. Key Modules
- **OnlineServicesNull** (Runtime): Null provider for Online Services (PostConfigInit).

## 3. Important Types & APIs
### Provider types (`OnlineServicesNull`, `OnlineServicesNullModule`)
- Role: Register and expose the null service implementation.
### Feature implementations (`AchievementsNull`, `AuthNull`, `LeaderboardsNull`, `LobbiesNull`, `SessionsNull`, `PresenceNull`, `StatsNull`, `TitleFileNull`, `UserFileNull`)
- Role: In-memory or placeholder implementations of Online Services feature interfaces.
### Utilities (`LobbyRegistryNull`, `NboSerializerNullSvc`, `OnlineServicesNullTypes`)
- Role: Helpers for lobby tracking and serialization for the null provider.

## 4. Typical usage patterns
- Enable when testing Online Services flows without hitting a real backend.
- Acquire the Null provider from `OnlineServicesRegistry` and exercise sessions/lobbies/achievements locally.

## 5. Version-specific notes (UE 5.7)
- No UE 5.7-specific notes; intentionally simple provider for testing.
