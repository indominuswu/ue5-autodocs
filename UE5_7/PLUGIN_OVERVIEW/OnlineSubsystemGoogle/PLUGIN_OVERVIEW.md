# Online Subsystem Google Plugin Overview

## 1. What this plugin does
- Supplies an OSSv1 provider for Google identity and external UI on Android/iOS/desktop.
- Includes common and platform-specific identity/login helpers plus REST fallback.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Platform OSS provider; games call `IOnlineSubsystem::Get("GOOGLE")` to use Google identity/external UI across supported platforms.

## 3. Key Modules
- **OnlineSubsystemGoogle** (Runtime): Google platform provider for Android/IOS/Linux/LinuxArm64/Mac/Win64.

## 4. Important Types & APIs
### Provider core (`FOnlineSubsystemGoogle`, `OnlineSubsystemGoogleModule`)
- Role: Registers the Google subsystem and exposes feature interfaces.
### Common implementations (`OnlineIdentityGoogleCommon`, `OnlineAccountGoogleCommon`, `OnlineExternalUIGoogleCommon`)
- Role: Shared identity/account/login UI helpers and type definitions.
### Platform-specific classes (`OnlineIdentityGoogle` for Android/iOS, `GoogleLoginWrapper`, `OnlineJniGoogleLogin`, `GoogleHelper`)
- Role: Handle native login/token exchange; present platform UI flows.
### REST variants (`OnlineIdentityGoogleRest`, `OnlineExternalUIInterfaceGoogleRest`)
- Role: REST-based login and UI integration for supported platforms.

## 5. Typical usage patterns
- Enable plugin, configure Google OAuth client IDs; retrieve subsystem via `IOnlineSubsystem::Get("GOOGLE")`.
- Use identity and external UI interfaces for sign-in; friends/other interfaces depend on Google service scopes.
- Choose platform-native or REST paths depending on target platform and configuration.

## 6. Version-specific notes (UE 5.7)
- No explicit 5.7 notes; platform allow list defined in plugin metadata.

