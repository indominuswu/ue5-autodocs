# Online Subsystem iOS Plugin Overview

## 1. What this plugin does
- Provides an OSSv1 provider for Apple Game Center on iOS/tvOS.
- Implements identity, friends, achievements, leaderboards, sessions, turn-based, cloud storage, purchases, and external UI flows using native frameworks.

## 2. Key Modules
- **OnlineSubsystemIOS** (Runtime): Game Center provider for iOS/tvOS.

## 3. Important Types & APIs
### Provider core (`FOnlineSubsystemIOS`, `OnlineSubsystemIOSModule`)
- Role: Registers the iOS subsystem and exposes feature interfaces.
### Identity/UI (`FOnlineIdentityInterfaceIOS`, `FOnlineExternalUIInterfaceIOS`)
- Role: Handle Game Center authentication and native UI dialogs.
### Features (`FOnlineSessionInterfaceIOS`, `FOnlineFriendsInterfaceIOS`, `FOnlineLeaderboardsInterfaceIOS`, `FOnlineAchievementsInterfaceIOS`, `FOnlineTurnBasedInterfaceIOS`, `FOnlineUserCloudInterfaceIOS`, `FOnlineSharedCloudInterfaceIOS`)
- Role: Implement Game Center sessions, friends, leaderboards, achievements, turn-based matches, and cloud saves.
### Store (`OnlinePurchaseIOS`, `OnlineStoreIOS`, `OnlineAppStoreUtils`, `StoreKitSwiftInterop`)
- Role: Manage in-app purchases through StoreKit.

## 4. Typical usage patterns
- Enable on iOS/tvOS builds; configure Game Center entitlements.
- Acquire subsystem via `IOnlineSubsystem::Get("IOS")`; authenticate via Game Center, then access sessions, friends, leaderboards, achievements, cloud storage, and purchases.
- Use turn-based interfaces for Game Center turn-based match workflows.

## 5. Version-specific notes (UE 5.7)
- No explicit 5.7-specific notes; platform allow list limited to iOS/tvOS in metadata.
