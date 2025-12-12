# Online Subsystem EOS Plugin Overview

## 1. What this plugin does
- Implements an OSSv1 provider for Epic Online Services (EOS) including sessions, stats, achievements, cloud, player reports/sanctions, and identity.
- Integrates with EOSVoiceChat, SocketSubsystemEOS, and EOS overlay support.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Platform OSS provider; games call `IOnlineSubsystem::Get("EOS")` to use EOS-backed sessions/identity/stats/cloud/moderation features.

## 3. Key Modules
- **OnlineSubsystemEOS** (Runtime): EOS OSS provider for Win64/Mac/Linux/LinuxArm64/Android.

## 4. Important Types & APIs
### `FOnlineSubsystemEOS` / `OnlineSubsystemEOSModule`
- Role: Provider registration and feature interface exposure for EOS.
### Feature implementations (`FOnlineSessionEOS`, `FOnlineStatsEOS`, `FOnlineAchievementsEOS`, `FOnlineLeaderboardsEOS`, `FOnlineTitleFileEOS`, `FOnlineUserCloudEOS`, `FOnlinePlayerReportEOS`, `FOnlinePlayerSanctionEOS`)
- Role: EOS-backed implementations of OSS session, stats, achievements, leaderboards, files, cloud, and moderation.
### Identity/settings helpers (`FOnlineIdentityEOS` via `UserManagerEOS`, `EOSSettings`, `OnlineSubsystemEOSTypes`)
- Role: Manage EOS credentials, product user/account IDs, and identity flows.
### Utilities (`NboSerializerEOS`, platform helper headers, `SocketSubsystemEOSUtils_OnlineSubsystemEOS`)
- Role: Serialization and socket/platform utilities tailored for EOS.

## 5. Typical usage patterns
- Enable plugin with EOSShared/EOSVoiceChat/SocketSubsystemEOS dependencies; configure EOS credentials in `EOSSettings`.
- Access subsystem via `IOnlineSubsystem::Get("EOS")` to drive sessions, stats, achievements, cloud files, and presence.
- Use player report/sanction interfaces when moderation flows are needed.

## 6. Version-specific notes (UE 5.7)
- No explicit 5.7-specific notes; platform allow list defined in plugin metadata.

