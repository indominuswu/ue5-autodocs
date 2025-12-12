# Online Services Epic Common Plugin Overview

## 1. What this plugin does
- Provides shared functionality used by both EOS Account Services and EOS Game Services Online Services providers.
- Adds common auth login option helpers and error handling for Epic services.
- Supplies platform factory support for creating the proper EOS-based provider per platform.

## 2. Editor/Runtime surfaces

- User-facing: No - Internal helper module for EOS Online Services providers (ID resolvers, login option helpers, platform factory); no standalone editor/runtime surfaces for game teams.

## 3. Key Modules
- **OnlineServicesEpicCommon** (Runtime): Shared Epic service utilities (PostConfigInit) for Android/IOS/Linux/LinuxArm64/Mac/Win64.

## 4. Important Types & APIs
### `OnlineServicesEpicCommon` / `OnlineServicesEpicCommonModule`
- Role: Module entry registering shared Epic service helpers.
### `EOSAuthLoginOptionsCommon`
- Role: Common auth login option builder for EOS-based providers.
### ID and error helpers (`EpicAccountIdResolver`, `EpicProductUserIdResolver`, `OnlineErrorEpicCommon`)
- Role: Resolve Epic IDs and normalize error handling across services.
### `OnlineServicesEpicCommonPlatformFactory`
- Role: Factory for constructing platform-appropriate Online Services providers using shared Epic logic.

## 5. Typical usage patterns
- Enabled transitively by EOS/EOSGS Online Services providers; rarely consumed directly.
- Use ID resolver helpers and login option builders when implementing additional Epic-backed services.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; platform allow list defined in metadata.

