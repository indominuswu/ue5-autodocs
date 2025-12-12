# Adjust Analytics Provider Plugin Overview

## 1. What this plugin does
- Integrates the Adjust analytics SDK for Android and iOS into Unreal.
- Provides platform-specific provider modules and editor settings.
- Exposes analytics events through the standard analytics provider interface.

## 2. Editor/Runtime surfaces
- User-facing: Yes - exposes `UAdjustSettings` in project settings and analytics providers developers configure/send events through the analytics API.

## 3. Key Modules
- **AndroidAdjust** (Runtime)
  - Role: Android implementation of the Adjust analytics provider.
- **IOSAdjust** (Runtime)
  - Role: iOS implementation of the Adjust analytics provider.
- **AdjustEditor** (Editor)
  - Role: Editor-side settings/configuration for Adjust.

## 4. Important Types & APIs

### `UAdjustSettings`
- Role: Project settings asset holding Adjust configuration (e.g., app tokens/platform flags).

### `FAndroidAdjustProvider` / `FIOSAdjustProvider`
- Role: Concrete analytics providers routing events to the Adjust SDK on each platform.

## 5. Typical usage patterns
- Enable the plugin and configure `UAdjustSettings` in project settings with your Adjust app tokens.
- At runtime, initialize analytics and send events through the engine analytics API; the multicast provider will route to Adjust on the active platform.
- Use the editor module to expose settings UI.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
