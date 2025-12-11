# Online Services EOS (Game Services) Plugin Overview

## 1. What this plugin does
- Implements Online Services provider for EOS Game Services only (no Epic Account Services dependency).
- Supplies EOSGS-backed implementations for achievements, auth, leaderboards, lobbies, sessions, stats, files, and player reports/sanctions.
- Includes EOSGS-specific lobby/session type definitions and socket utils.

## 2. Key Modules
- **OnlineServicesEOSGS** (Runtime): EOS Game Services provider (PostConfigInit) for Win64/Mac/Linux/LinuxArm64/Android.

## 3. Important Types & APIs
### `OnlineServicesEOSGS` / `OnlineServicesEOSGSModule`
- Role: Provider entry point wiring EOSGS components.
### Feature implementations (`AuthEOSGS`, `AchievementsEOSGS`, `LeaderboardsEOSGS`, `LobbiesEOSGS`, `SessionsEOSGS`, `StatsEOSGS`, `TitleFileEOSGS`, `UserFileEOSGS`, `ExternalUIEOSGS`)
- Role: EOSGS-backed Online Services features using EOS SDK calls.
### Moderation types (`PlayerReportsEOSGS`, `PlayerSanctionsEOSGS`, `LobbiesEOSGSTypes`, `SessionsEOSGSTypes`)
- Role: Report/sanction handling and EOSGS-specific lobby/session data models.
### Platform helpers (`EpicProductUserIdResolverEOSGS`, `SocketSubsystemEOSUtils_OnlineServicesEOSGS`, `IOSEOSAuthLoginOptions`)
- Role: ID resolution, socket integration, and platform-specific auth options.

## 4. Typical usage patterns
- Enable with OnlineServices and EOSShared; fetch the EOSGS provider from `OnlineServicesRegistry` for game-services-only deployments.
- Configure EOS credentials and call feature interfaces for lobbies, sessions, achievements, stats, and file services.
- Use player report/sanction APIs where moderation flows are required.

## 5. Version-specific notes (UE 5.7)
- No explicit 5.7-specific notes; plugin is platform-limited per metadata and depends on EOSShared/SocketSubsystemEOS.
