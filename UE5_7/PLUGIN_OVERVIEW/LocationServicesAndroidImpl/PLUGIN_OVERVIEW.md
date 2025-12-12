# Mobile Location Services - Android Implementation Plugin Overview

## 1. What this plugin does

- Android-specific implementation behind the cross-platform `LocationServices` Blueprint API.
- Bridges UE location requests to Android’s location manager via JNI, handling permissions and accuracy modes.
- Provides editor settings to configure coarse/fine location usage and whether updates are enabled.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Android developers enable it and use `ULocationServices` Blueprint APIs with `ULocationServicesAndroidSettings` to request location data/permissions.

## 3. Key Modules

- **LocationServicesAndroidImpl** (Runtime, Android)
  - Role: Supplies `ULocationServicesImpl` for Android; forwards Init/Start/Stop/Query calls to platform code and broadcasts location change events.
  - Notable types: `ULocationServicesAndroidImpl`, JNI glue in `AndroidJniLocationServices`.
- **LocationServicesAndroidEditor** (Editor)
  - Role: Exposes project settings for Android location services and registers them in the editor.
  - Notable types: `ULocationServicesAndroidSettings`, `FLocationServicesAndroidEditorModule`.

## 4. Important Types & APIs

### `ULocationServicesAndroidSettings`

- Role: Config object for Android location permissions and update behavior.
- Key properties: `bCoarseLocationEnabled`, `bFineLocationEnabled`, `bLocationUpdatesEnabled`.

### `ULocationServicesAndroidImpl`

- Role: Platform implementation of `ULocationServicesImpl` on Android.
- Key functions: `InitLocationServices`, `StartLocationService`, `StopLocationService`, `GetLastKnownLocation`, `IsLocationAccuracyAvailable`, `IsLocationServiceEnabled`.
- Behavior: Calls into `AndroidThunkJava_*` functions defined in `LocationServicesAndroidImpl_UPL.xml` to configure the Android location manager and forwards updates back to `ULocationServices::OnLocationChanged`.

## 5. Typical usage patterns

- Enable both `LocationServicesBPLibrary` and this Android implementation when building for Android.
- Configure coarse/fine permission usage under Project Settings → Location Services - Android.
- From Blueprints (via `ULocationServices`), call `InitLocationServices`, then `StartLocationServices`; bind to the `OnLocationChanged` delegate for updates. Stop services when no longer needed.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

