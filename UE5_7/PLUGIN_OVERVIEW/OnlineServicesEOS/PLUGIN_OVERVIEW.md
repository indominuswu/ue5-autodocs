# Online Services EOS Plugin Overview

## 1. What this plugin does
- Implements Online Services provider targeting Epic Online Services accounts and game services.
- Provides EOS-backed Auth, Commerce, Presence, Social, External UI, and user info integration.
- Uses shared EOS ID resolvers for Epic Account IDs and Product User IDs.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Game teams opt into this Online Services provider to call EOS-backed Auth/Presence/Social/etc. through `OnlineServicesEOS` feature interfaces.

## 3. Key Modules
- **OnlineServicesEOS** (Runtime): EOS service provider implementation (PostConfigInit) for Win64/Mac/Linux/LinuxArm64/Android.

## 4. Important Types & APIs
### `OnlineServicesEOS` / `OnlineServicesEOSModule`
- Role: Provider entry point registering EOS-backed feature components.
### Feature implementations (`AuthEOS`, `CommerceEOS`, `PresenceEOS`, `SocialEOS`, `ExternalUIEOS`, `UserInfoEOS`)
- Role: EOS-backed versions of Online Services feature interfaces.
### Identity helpers (`AccountIdEOS`, `OnlineIdEOS`, `EpicAccountIdResolverEOS`, `EpicProductUserIdResolverEOS`)
- Role: Wrap EOS account/product user identifiers and resolve them to Online Services IDs.

## 5. Typical usage patterns
- Enable alongside OnlineServices and EOSShared; obtain the EOS provider from `OnlineServicesRegistry` and use feature interfaces.
- Configure EOS credentials/settings via EOSShared/EOS platform config; then call Auth/Presence/Lobbies/etc. through the provider.

## 6. Version-specific notes (UE 5.7)
- No explicit 5.7-specific notes; platform allow list matches plugin metadata.

