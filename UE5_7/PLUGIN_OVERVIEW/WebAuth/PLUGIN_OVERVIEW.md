# Web Authentication Plugin Overview

## 1. What this plugin does

- Provides a platform abstraction for authenticated web sessions (Windows, iOS, Android) with delegate callbacks.
- Allows saving/loading credentials and clearing login cookies for web-based flows.
- Supplies platform-specific implementations selected at compile time.

## 2. Key Modules

- **WebAuth** (Runtime)
  - Role: Core interfaces (`IWebAuth`) and platform bindings for launching auth sessions and managing credentials; enabled on Win64/iOS/Android (client only).

## 3. Important Types & APIs

### `IWebAuth`
- Role: Interface exposing `AuthSessionWithURL` (launch browser-based auth and return redirect URL), `SaveCredentials`, `LoadCredentials`, and `DeleteLoginCookies`.
- Platform selection is handled via `PlatformWebAuth.h` (includes iOS/Android-specific implementations or `NullPlatformWebAuth`).

### Platform modules
- Role: `IOSPlatformWebAuth`, `AndroidPlatformWebAuth`, and `NullPlatformWebAuth` provide concrete behaviors per platform.

## 4. Typical usage patterns

- Enable the plugin for client builds. Obtain the platform `IWebAuth` implementation and call `AuthSessionWithURL` with the auth URL and scheme; bind `FWebAuthSessionCompleteDelegate` to receive the redirect and success flag.
- Use `SaveCredentials`/`LoadCredentials` to persist tokens between sessions; call `DeleteLoginCookies` when revoking logins or changing environments.
- Server targets are excluded; intended for client authentication flows.

## 5. Version-specific notes (UE 5.7)

- Plugin is non-experimental and disabled by default. No UE 5.7-specific notes were found beyond current platform guards.
