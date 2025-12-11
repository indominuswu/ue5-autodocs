# Online Subsystem GooglePlay Plugin Overview

## 1. What this plugin does
- Implements Android-only OSSv1 provider for Google Play Games Services.
- Provides achievements, leaderboards, identity, external UI, and in-app purchase/store support.

## 2. Key Modules
- **OnlineSubsystemGooglePlay** (Runtime): Google Play provider (Android only).

## 3. Important Types & APIs
### Provider core (`FOnlineSubsystemGooglePlay`, `OnlineSubsystemGooglePlayModule`)
- Role: Registers the Google Play subsystem and exposes feature interfaces.
### Identity/UI (`FOnlineIdentityInterfaceGooglePlay`, `OnlineExternalUIInterfaceGooglePlay`, `GooglePlayGamesWrapper`, `OnlineJniGooglePlayGamesWrapper`)
- Role: Manage Google Play login and present native UI flows.
### Achievements/Leaderboards (`OnlineAchievementsInterfaceGooglePlay`, `OnlineLeaderboardInterfaceGooglePlay`, async tasks for query/write/flush)
- Role: Implement achievements and leaderboard operations using Google Play APIs.
### Store/Purchase (`OnlineStoreGooglePlay`, `OnlinePurchaseGooglePlay`, `OnlineStoreGooglePlayCommon`, `OnlineJniGooglePlayStoreHelper`)
- Role: Handle in-app purchases and store catalog interactions.

## 4. Typical usage patterns
- Enable plugin on Android, ensure Google Play Games dependencies configured.
- Obtain subsystem via `IOnlineSubsystem::Get("GOOGLEPLAY")`; login via identity/external UI, then drive achievements, leaderboards, and purchases.

## 5. Version-specific notes (UE 5.7)
- Android-only per plugin metadata; no additional 5.7-specific notes.
