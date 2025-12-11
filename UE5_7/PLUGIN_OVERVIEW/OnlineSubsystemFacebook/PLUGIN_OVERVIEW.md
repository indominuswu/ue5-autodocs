# Online Subsystem Facebook Plugin Overview

## 1. What this plugin does
- Provides an OSSv1 provider for Facebook login, friends, sharing, and user info across Android/iOS/Win64.
- Offers REST, platform-native (Android/iOS), and common helper implementations.

## 2. Key Modules
- **OnlineSubsystemFacebook** (Runtime): Facebook OSS provider with platform-specific implementations.

## 3. Important Types & APIs
### Provider core (`FOnlineSubsystemFacebook`, `OnlineSubsystemFacebookModule`)
- Role: Registers the Facebook subsystem and manages provider lifecycle.
### Common feature implementations (`OnlineIdentityFacebookCommon`, `OnlineFriendsFacebookCommon`, `OnlineSharingFacebookCommon`, `OnlineAccountFacebookCommon`, `OnlineExternalUIFacebookCommon`, `OnlineUserFacebookCommon`)
- Role: Shared logic for identity, friends, sharing, UI, and account management.
### Platform-specific classes (`OnlineIdentityFacebook` for Android/iOS, `OnlineExternalUIInterfaceFacebook`, `OnlineJniFacebookLogin`, `FacebookHelper`)
- Role: Handle native login, UI presentation, and JNI/ObjC bridging.
### REST variants (`OnlineIdentityFacebookRest`, `OnlineExternalUIInterfaceFacebookRest`, etc.)
- Role: REST-based fallback implementations for identity/friends/sharing/user retrieval.

## 4. Typical usage patterns
- Enable plugin and configure Facebook App ID/secret; obtain subsystem via `IOnlineSubsystem::Get("FACEBOOK")`.
- Use identity interface to sign in; leverage friends/sharing/user info interfaces and optional REST fallbacks.
- Integrate external UI helpers for login dialogs on Android/iOS/Win64.

## 5. Version-specific notes (UE 5.7)
- No explicit 5.7 notes; platform allow list includes Android, iOS, and Win64 per metadata.
