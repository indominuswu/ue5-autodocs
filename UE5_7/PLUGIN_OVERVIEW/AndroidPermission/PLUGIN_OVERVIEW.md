# Android Runtime Permission Plugin Overview

## 1. What this plugin does
- Adds Blueprint-accessible helpers to request and query Android runtime permissions.
- Handles permission request callbacks for Android 6.0+ runtime permission model.
- Provides a lightweight runtime module (enabled by default) for Android builds.

## 2. Key Modules
- **AndroidPermission** (Runtime, Default)
  - Role: Exposes permission request APIs and integrates with Android JNI callbacks.

## 3. Important Types & APIs
- `UAndroidPermissionFunctionLibrary`
  - Role: BlueprintFunctionLibrary exposing permission requests and status checks.
- `UAndroidPermissionCallbackProxy`
  - Role: Async Blueprint proxy handling permission request completion results.
- `FAndroidPermissionModule`
  - Role: Runtime module startup/shutdown and logging category (`LogAndroidPermission`).

## 4. Typical usage patterns
- Enable the plugin (default) in Android projects; call `AcquirePermissions`/similar Blueprint nodes to request permissions at runtime.
- Bind to the callback proxy to handle granted/denied results before proceeding with features that require protected access.
- Combine with manifest declarations for permissions that still require manifest entries.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
