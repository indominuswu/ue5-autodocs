# Steam Shared Module Plugin Overview

## 1. What this plugin does
- Shared Steamworks loader used by Steam-related plugins (e.g., OnlineSubsystemSteam, SteamSockets, SteamController).
- Handles loading/unloading of Steam client and server DLLs and exposes handles to other modules.
- Provides helper classes that manage Steam API lifetime for both client and dedicated server contexts.

## 2. Key Modules
- **SteamShared** (Runtime, PreDefault) – Loads Steam client/server binaries, exposes accessors, and tracks instance lifetimes; enabled on Win64/Mac/Linux except Win64 ARM64.

## 3. Important Types & APIs
- `FSteamSharedModule` – Runtime module that loads Steam DLLs, exposes `ObtainSteamClientInstanceHandle()` / `ObtainSteamServerInstanceHandle()`, reports DLL load state, and guards dynamic reload.
- `FSteamClientInstanceHandler` / `FSteamServerInstanceHandler` – RAII helpers that initialize and tear down Steam client/server API instances and cache ports for bookkeeping.
- `FSteamInstanceHandlerBase` – Common base handling initialization flags, cleanup eligibility, and destruction.

## 4. Typical usage patterns
- Enable `SteamShared` when building plugins that require Steamworks (OnlineSubsystemSteam, SteamSockets, SteamController).
- Call `FSteamSharedModule::Get()` and request a client or server handle before using Steamworks APIs; keep the handler alive for the duration of Steam usage.
- Useful for dedicated servers that optionally load client DLLs (guarded by platform checks and `CanLoadClientDllsOnServer`).

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview reflects the current source.

