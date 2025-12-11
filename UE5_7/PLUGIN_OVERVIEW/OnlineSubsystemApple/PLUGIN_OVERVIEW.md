# Online Subsystem Apple Plugin Overview

## 1. What this plugin does
- Supplies an OSSv1 provider for Sign in with Apple across Mac/iOS/tvOS.
- Implements identity and external UI flows for Apple sign-in.

## 2. Key Modules
- **OnlineSubsystemApple** (Runtime): Apple platform subsystem for Mac/iOS/tvOS.

## 3. Important Types & APIs
### `FOnlineSubsystemApple` / `FOnlineSubsystemAppleModule`
- Role: Provider setup/registration for Apple platforms.
### `FOnlineIdentityInterfaceApple` / `OnlineSubsystemAppleTypes`
- Role: Handles Apple ID authentication tokens and platform-specific identity data.
### `FOnlineExternalUIInterfaceApple`
- Role: Presents Apple sign-in UI as part of the authentication flow.

## 4. Typical usage patterns
- Enable on Mac/iOS/tvOS targets; configure Apple Sign-In keys.
- Retrieve subsystem via `IOnlineSubsystem::Get("APPLE")`, then use the identity/external UI interfaces for login and token retrieval.

## 5. Version-specific notes (UE 5.7)
- No explicit 5.7 notes; platform allow list matches plugin metadata.
