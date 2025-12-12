# Online Services Plugin Overview

## 1. What this plugin does
- Provides the OSSv2 Online Services interface layer and common implementations.
- Defines async op framework, service registries, schemas, and common feature implementations (sessions, lobbies, achievements, stats, presence, auth, commerce, files).
- Includes engine utilities for LAN sessions and world-context-scoped caches.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Exposes the OSSv2 developer-facing API (`OnlineServicesRegistry`, feature interfaces for Sessions/Lobbies/Auth/etc.) that games consume directly or extend for provider implementations.

## 3. Key Modules
- **OnlineServicesInterface** (Runtime): Core interfaces (`OnlineServices`, `OnlineAsyncOpHandle`, schema types) and registry.
- **OnlineServicesCommon** (Runtime): Shared service implementations and component system for common feature sets.
- **OnlineServicesCommonEngineUtils** (Runtime): Engine-side helpers (e.g., `SessionsLAN`, `WorldContextScopedObjectCache`).

## 4. Important Types & APIs
### Interfaces (`OnlineServices`, `OnlineServicesRegistry`, `OnlineAsyncOpHandle`)
- Role: Entry points to service providers, async op lifecycle, and service registration.
### Feature interfaces (`Sessions`, `Lobbies`, `Auth`, `Achievements`, `Presence`, `Stats`, `Leaderboards`, `Commerce`, `TitleFile`, `UserFile`, `UserInfo`, `Social`, `Privileges`)
- Role: Provider-agnostic contracts for online features with rich type definitions (`Schema`, `SchemaTypes`, `OnlineResult`).
### Common implementations (`SessionsCommon`, `LobbiesCommon`, `AuthCommon`, `AchievementsCommon`, `PresenceCommon`, etc.)
- Role: Base classes and helpers for provider-specific services including `OnlineComponent`/`OnlineComponentRegistry` and async op queues/caches.
### Engine utils (`SessionsLAN`, `WorldContextScopedObjectCache`)
- Role: LAN session helper implementation and world-context-aware object caching.

## 5. Typical usage patterns
- Enable as a dependency of specific provider plugins (EOS, Null, OSS Adapter, etc.).
- Instantiate a provider via `OnlineServicesRegistry`, then access feature interfaces (Sessions, Lobbies, Auth, etc.) and drive operations with `OnlineAsyncOpHandle`.
- Use common implementations as bases when authoring a new Online Services provider.

## 6. Version-specific notes (UE 5.7)
- No explicit 5.7-specific notes; represents the current OSSv2 service stack in this source tree.

