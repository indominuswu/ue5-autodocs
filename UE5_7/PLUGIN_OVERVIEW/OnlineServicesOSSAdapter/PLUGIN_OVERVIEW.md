# Online Services OSS Adapter Plugin Overview

## 1. What this plugin does
- Bridges legacy Online Subsystem (OSSv1) implementations into the OSSv2 Online Services interface.
- Wraps OSS feature interfaces and adapts them to Online Services schemas.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Developers pick this provider to surface existing OSSv1 platform plugins through the OSSv2 `OnlineServices` API during migrations.

## 3. Key Modules
- **OnlineServicesOSSAdapter** (Runtime): Adapter provider (PostConfigInit) that exposes OSS backends through Online Services APIs.

## 4. Important Types & APIs
### Provider types (`OnlineServicesOSSAdapter`, `OnlineServicesOSSAdapterModule`)
- Role: Register adapter and route Online Services requests to OSS implementations.
### Feature adapters (`AuthOSSAdapter`, `AchievementsOSSAdapter`, `LeaderboardsOSSAdapter`, `SessionsOSSAdapter`, `PresenceOSSAdapter`, `SocialOSSAdapter`, `CommerceOSSAdapter`, `TitleFileOSSAdapter`, `UserFileOSSAdapter`, `PrivilegesOSSAdapter`, `ExternalUIOSSAdapter`)
- Role: Translate Online Services contracts to corresponding OSS calls.
### Utilities (`OnlineIdOSSAdapter`, `DelegateAdapter`, `MulticastAdapter`, `ErrorsOSSAdapter`)
- Role: ID translation and delegate/multicast bridging between systems.

## 5. Typical usage patterns
- Enable when migrating to Online Services while still relying on existing OSS platform plugins.
- Select the OSS Adapter provider in `OnlineServicesRegistry`; existing OSS configuration drives the underlying platform behavior.

## 6. Version-specific notes (UE 5.7)
- No explicit 5.7 notes; designed as a compatibility layer during transition to OSSv2.

