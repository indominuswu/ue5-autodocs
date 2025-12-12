# Android Fetch Background Download Plugin Overview

## 1. What this plugin does
- Enables BackgroundHTTP requests on Android while the app is backgrounded using the platform Fetch API.
- Provides a modular feature implementation that bridges UE's BackgroundHTTP interfaces to Android Fetch workers.
- Manages platform-specific request, response, and manager classes for background transfers.

## 2. Editor/Runtime surfaces
- User-facing: No - platform backend for BackgroundHTTP using Android Fetch; no editor tools or direct Blueprint/runtime APIs beyond existing BackgroundHTTP interfaces.

## 3. Key Modules
- **AndroidFetchBackgroundDownload** (RuntimeNoCommandlet)
  - Role: Registers the Android Fetch-based BackgroundHTTP implementation and exposes platform request/response handling.

## 4. Important Types & APIs
- `FAndroidPlatformBackgroundHttpManager`
  - Role: Central manager for background download tasks; orchestrates Fetch worker interactions.
- `FAndroidPlatformBackgroundHttpRequest` / `FAndroidPlatformBackgroundHttpResponse`
  - Role: Platform-specific request/response wrappers used by BackgroundHTTP.
- `FAndroidPlatformBackgroundHttpModularFeatureWrapper`
  - Role: Registers the Android Fetch implementation as a modular feature.
- `FAndroidJniDownloadUEDownloadWorker`
  - Role: JNI bridge for background worker communication.

## 5. Typical usage patterns
- Enable the plugin when BackgroundHTTP downloads must continue while the Android app is backgrounded.
- Use UE's BackgroundHTTP APIs as usual; the plugin routes work to the Android Fetch implementation without additional user code.
- Ensure Android permissions/network policies allow background transfers.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
