# Google Cloud Messaging Plugin Overview

## 1. What this plugin does

- Adds support for receiving remote push notifications via Google Cloud Messaging on Android.
- Exposes a lightweight API to register for and handle notification events.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Android developers enable it and initialize `FGoogleCloudMessaging` to register for and handle push notification payloads.

## 3. Key Modules

- **GoogleCloudMessaging** (Runtime)  
  - Role: Notification registration/handling wrapper for GCM.  
  - Notable types: `FGoogleCloudMessaging`.

## 4. Important Types & APIs

### `FGoogleCloudMessaging`

- Role: Primary interface for initializing GCM integration and listening for incoming messages.
- Key functions/properties: Register/unregister for notifications, callbacks for received payloads (per the implementation).

## 5. Typical usage patterns

- Enable the plugin for Android builds; during app startup, initialize `FGoogleCloudMessaging` to register for push notifications.
- Implement callbacks/handlers to process incoming messages and route them to gameplay/UI as needed.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

