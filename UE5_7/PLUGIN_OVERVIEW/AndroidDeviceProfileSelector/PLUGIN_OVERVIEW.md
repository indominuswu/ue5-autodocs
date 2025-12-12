# Android Device Profile Selector Plugin Overview

## 1. What this plugin does
- Selects device profiles at startup based on detected Android hardware and runtime characteristics.
- Exposes profile matching helpers for Android GPU, OS version, make/model, Vulkan/GL support, resolution, and other device properties.
- Provides editor utilities and commandlets to author and validate matching rules.

## 2. Editor/Runtime surfaces
- User-facing: Yes - developer-facing device profile selection with runtime helper `FAndroidDeviceProfileSelector` and editor/commandlet tools for authoring rules.

## 3. Key Modules
- **AndroidDeviceProfileSelectorRuntime** (RuntimeNoCommandlet, PostConfigInit)
  - Role: Applies matching logic on device startup to choose the best profile.
- **AndroidDeviceProfileSelector** (Editor)
  - Role: Editor-side hooks for profile selection UI and rule authoring.
- **AndroidDeviceProfileCommandlets** (Editor)
  - Role: Commandlets for testing or generating profile data.

## 4. Important Types & APIs
- `FAndroidDeviceProfileSelector`
  - Role: Static helpers to gather selector properties and compute the matching profile.
  - Key functions: `FindMatchingProfile`, `GetNumProfiles`, `SetSelectorProperties`, `GetSelectorProperties`.
- Selector property keys (`FAndroidProfileSelectorSourceProperties`)
  - Include GPU family, GL/Vulkan versions, Android version, make/model/build number, Houdini use, chipset, HMD name, RAM, SM5 availability, resolution, insets, and Vulkan quality indicators.

## 5. Typical usage patterns
- Enable the plugin (on by default) and configure device profiles in the Android Device Profile asset list.
- At startup, the runtime module evaluates device characteristics and assigns the appropriate profile before config initialization completes.
- Use editor tooling/commandlets to test matching logic against target device parameters.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview reflects the UE 5.7 source tree.
