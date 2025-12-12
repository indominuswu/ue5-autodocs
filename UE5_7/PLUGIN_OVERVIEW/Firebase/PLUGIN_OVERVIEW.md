# Firebase Plugin Overview

## 1. What this plugin does
- Provides Firebase-based remote notification support for Android and iOS targets.
- Exposes a runtime module interface to access Firebase notification token updates.
- Ships platform-specific implementations (notably iOS notification bridge) and third-party headers.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Mobile developers enable it and bind to `IFirebaseModuleInterface::OnTokenUpdate` to receive Firebase push tokens (with platform config files supplied).

## 3. Key Modules
- **Firebase** (Runtime; Android/iOS)
  - Role: Core module exposing notification token updates and bootstrapping platform bindings.
  - Notable types: `IFirebaseModuleInterface`, platform bridge `EpicFirebaseIOSNotifications`.

## 4. Important Types & APIs

### `IFirebaseModuleInterface`
- Role: Module interface accessible via `IFirebaseModuleInterface::Get()`.
- Key features: `StartupModule()`/`ShutdownModule()` lifecycle and `OnTokenUpdate` multicast delegate broadcasting `(FString Token, FString Platform)` changes.
- Availability helpers: `IsAvailable()` guards module access.

### `EpicFirebaseIOSNotifications`
- Role: iOS-side bridge header for Firebase notification handling.
- Used internally when targeting iOS to register and forward notifications/tokens.

## 5. Typical usage patterns
- Enable the plugin for mobile builds (Android/iOS) and include Firebase SDK dependencies in your project setup.
- On startup, bind to `IFirebaseModuleInterface::Get().OnTokenUpdate` to receive refreshed push notification tokens.
- Configure platform-specific Firebase config files (e.g., `google-services.json` / `GoogleService-Info.plist`) per standard Firebase setup; the plugin supplies the Unreal-facing hook.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific behaviors found; plugin is disabled by default and limited to Android/iOS platforms in the current source.

