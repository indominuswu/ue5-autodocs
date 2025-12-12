# Google ARCore Services Plugin Overview

## 1. What this plugin does

- Adds support for Google ARCore Cloud services (e.g., Cloud Anchors) on top of the base ARCore integration.
- Provides Blueprint-callable APIs for managing cloud-hosted AR pins/anchors.
- Includes editor settings for service configuration.

## 2. Editor/Runtime surfaces

- User-facing: Yes - AR developers configure `UGoogleARCoreServicesEditorSettings` and call `UGoogleARCoreServicesFunctionLibrary` to host/resolve Cloud Anchors during sessions.

## 3. Key Modules

- **GoogleARCoreServices** (Runtime)  
  - Role: Cloud service management, Blueprint API surface, and utility helpers.  
  - Notable types: `UGoogleARCoreServicesFunctionLibrary`, `UGoogleARCoreServicesTypes`, `FGoogleARCoreCloudARPinManager`, `FGoogleARCoreServicesManager`, `FGoogleARCoreServicesModule`, `UGoogleARCoreServicesEditorSettings`.

## 4. Important Types & APIs

### `UGoogleARCoreServicesFunctionLibrary`

- Role: Blueprint entry points for hosting, resolving, and managing cloud-based AR pins/anchors.
- Key functions: Cloud anchor hosting/resolution, asynchronous callbacks, status/result queries defined in `UGoogleARCoreServicesTypes`.

### `FGoogleARCoreCloudARPinManager`

- Role: Manages the lifecycle of Cloud Anchors within the AR session, coordinating host/resolve requests.

### `UGoogleARCoreServicesEditorSettings`

- Role: Editor settings object for configuring ARCore Services credentials/options.

## 5. Typical usage patterns

- Enable the plugin alongside GoogleARCore; configure ARCore Services settings (API keys/project info) in editor settings.
- In Blueprint, call `UGoogleARCoreServicesFunctionLibrary` to host or resolve Cloud Anchors and react to the resulting status codes.
- Use the pin manager to keep track of active cloud anchors during AR sessions.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

